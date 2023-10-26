---
layout: single
title: Intensity Mapping
katex: True
permalink: /posts/intensity_mapping/
toc: True
toc_sticky: True
---

21 cm cosmology studies the redshifted 21 cm-wavelength photons that are emitted in a hyperfine transition of atomic hydrogen atoms (HI). 
The transition occurs when an electron in the excited spin triplet state flips its spin relative to the proton and falls into the singlet state. 
While this transition is quantum mechanically `forbidden' to first order, a very large number of neutral hydrogen atoms in massive clouds render 
the signal observable.

The hyperfine transition can be used to trace the matter field through a technique called 21 cm intensity mapping 
(IM) [(Santos et al. 2015)](https://pos.sissa.it/215/019). It is possible since the spin transition in HI is optically 
thin [(Furlanetto et al. 2006)](https://ui.adsabs.harvard.edu/abs/2006PhR...433..181F), meaning that 21 cm photons are unlikely to be absorbed/emitted more 
than once as they travel to our telescopes. Therefore, full 3D mappings of the 21 cm line become possible, with the redshift of the signal providing information 
about the line of sight distance. Unlike galaxy redshift surveys, there is no need to resolve individual galaxies, which is often required only to determine 
their redshift. By mapping the unresolved emission of all HI at each frequency of observation and using the observed frequency-redshift 
relation $$\nu= \nu_{21}/(1+z)$$, we can directly map to the corresponding redshift. This is further facilitated by the ease at which spectral resolution can be 
obtained in radio astronomy.

Ongoing and upcoming 21 cm IM experiments such as HIRAX [(Newburgh et al. 2016)](dx.doi.org/10.1117/12.2234286), 
PUMA [(Bandura et al. 2019)](https://arxiv.org/abs/1907.12559), CHIME [(Collaboration et al. 2022)](https://arxiv.org/abs/2202.01242) and [(SKA)](https://www.skao.int/) 
[(Combes et al. 2021)](https://arxiv.org/abs/2107.03915) are set to yield a wealth of insights into cosmology and astrophysics. With minimal angular resolution 
requirements and expansive fields of view, these instruments can efficiently map vast cosmological volumes. The 21 cm signal in the post-reionization era 
(and also during reionization) holds great promise for studying alternative dark matter (DM) scenarios. The 21 cm signal is not only sensitive to DM decays, 
annihilation processes [(List et al. 2020)](https://ui.adsabs.harvard.edu/abs/2020ApJ...904..153L/abstract) or interactions between DM and standard model 
particles [(Munoz et al. 2018)](https://ui.adsabs.harvard.edu/abs/2018arXiv180210094M/abstract). It can also probe DM models that result in a suppression of the 
small-scale matter power spectrum [(Bauer et al. 2021)](https://ui.adsabs.harvard.edu/abs/2021MNRAS.500.3162B/abstract), which are the focus of this paper.

In our investigation, we run $$N$$-body hydrodynamical simulations of CDM and FDM cosmologies (similar to [this page](halos.md)), exploring a range of axion masses 
spanning from $$m=10^{-22}$$ eV to $$2\times 10^{-21}$$ eV. Note that in this mass range, FDM is effectively ruled out as comprising $$100$$\% of the DM 
content, as discussed in [Dome et al. (2022)](https://academic.oup.com/mnras/article/519/3/4183/6961063). However, in this study, the FDM-like modeling approach will allow 
us to elucidate trends associated with the axion mass $m$ across a variety of observables. These trends are expected to stay robust even if FDM constitutes only a 
subcomponent of the DM. 

In order to extract the maximum information from IM surveys, it is critical to reliably model the spatial distribution of HI. In our modeling approach, we 
largely follow the cell-based HI post-processing techniques from [Villaescusa-Navarro et al. (2018)](https://ui.adsabs.harvard.edu/abs/2018ApJ...866..135V) and
[Diemer et al. (2019)](https://ui.adsabs.harvard.edu/abs/2019MNRAS.487.1529D/abstract). We also harness the potential of machine learning (ML) 
and use normalizing flows, a generative ML model introduced by [Agnelli et al. (2010)](dx.doi.org/10.1137/100783522), to capture intricate 
structures resulting from non-linear physics, facilitating the *conditional* generation of HI maps with varying axion masses. Specifically, 
we use a slightly modified version of the conditional normalizing flow framework HIGlow [(Friedman et al. 2022)](https://arxiv.org/abs/2211.12724) and show that 
the efficiency of the model in sample generation, coupled with its inherent likelihood-based framework, streamlines statistical 
inference for parameter estimation and constraint prediction from 21 cm IM experiments. We assess the generated HI maps against 
external simulation data, utilizing metrics like HI mass probability density functions and power spectra, validating the prowess of 
the model across a broad spectrum of mass scales and spatial dimensions. This affirms its efficacy in characterizing HI distributions 
for forthcoming parameter forecasting endeavors.

The following results are based on [Dome et al. (2023)](https://arxiv.org/abs/2310.11502). For an overview of CDM and FDM hydrodynamical simulations,
the modeling of hydrogen phases and its link to 21 cm physics and details on conditional normalizing flows the reader is referred to the paper.

## HIGlow Modeling of HI

In Fig. 1, we show 2D HI mass projections of post-processed $$\Lambda$$CDM and cFDM simulation data. We choose a frequency 
channel $$[\nu_{0}-\Delta/2, \nu_{0}+\Delta/2]$$ of width $$\Delta \nu = 272$$ kHz around the central frequency $$\nu_0 = \nu_{21}/(1+z)$$, 
where $$\nu_{21} = 1420.406$$ MHz is the rest frequency of the 21 cm line. The channel width corresponds to a comoving width of

$$\Delta L = r_{\nu_{21}-\Delta \nu/2} - r_{\nu_{21}+\Delta \nu/2} \approx 2.5 \ h^{-1}\text{Mpc},$$

where $$r_{\nu}$$ is the comoving distance to redshift

$$z=\nu_{21}/\nu - 1,$$

for the observational frequency $$\nu$$. We take the same slice of width $$\Delta L$$ along the $$x$$-direction from the four hydrodynamic 
snapshots at $$z=4.94$$, PCS-paint the HI particle data onto a 3D grid [(Hand et al. 2018)](https://ui.adsabs.harvard.edu/abs/2018AJ....156..160H/abstract)), and 
project along the $$x$$-direction. We see how small-scale structure is visibly suppressed as the axion mass $$m$$ is reduced from 
infinity (CDM, top left) down to $$m = 10^{-22}$$ eV (bottom right).

| <img src="/assets/images/imapping/HImaps.png" width="850" height="550"> |
|:--:| 
| *Fig. 1: HI mass maps in CDM and cFDM cosmologies at the post-reionization redshift of $$z=4.94$$. The width of the projected slice $$\Delta L \approx 2.5 \ h^{-1}$$Mpc corresponds to a channel width of $$\Delta \nu = 272$$ kHz. Redshift-space distortions (RSDs) are included by displacing Voronoi cells accordingly.* |

Fig. 2 shows some sigmoid-normalized $$64\times 64$$ HI training maps in the top four rows across the CDM and cFDM cosmologies at $$z=4.94$$. 
The bottom four rows show generated HIGlow HI samples with identical seeds across the cosmologies. There are no diverging pixels or other 
visual anomalies. Without the rescaled sigmoid in the conditional affine coupling layer, an alternative approach would have been to apply 
image clipping, constraining pixel values to fall within predefined maximum and minimum ranges, after each of the six flow blocks in 
the generative reverse flow. However, this would have come at the cost of losing important image features with each subsequent clipping 
operation.

The samples visually have very similar features compared to the input training data. The model has learned the effect of changing the 
axion mass $$m$$ on the HI maps, and the characteristic suppression of small-scale structure at lower axion mass is apparent. We also 
show HIGlow samples for a synthetic cosmology corresponding to a new axion mass $$m=3\times 10^{-22}$$ eV. The generated samples display 
subtle small-scale features that occupy an intermediate position between those of the $$m=10^{-22}$$ eV and $$m=7\times 10^{-22}$$ eV samples, 
aligning with our expectations. We have conducted comprehensive validation tests, the results of which are outlined in the following.

| <img src="/assets/images/imapping/TrainsGensFinal.png" width="450" height="850"> |
|:--:| 
| *Fig. 2: Simulated data training samples (top four rows) and generated samples with HIGlow (bottom four rows) in the various cosmologies at $$z=4.94$$. The $$64^2$$ maps are $$2.5 \ h^{-1}$$Mpc a side. We add HIGlow samples for a conditional axion mass $$m = 3\times 10^{-22}$$ eV. This case does not have corresponding simulation data, illustrated by crosses. The axion mass $$m$$ decreases from right to left, with increased small-scale suppression.* |

To ensure that the statistics of the generated HI maps follow the statistics of the simulation data, we use two validation metrics: 
HI mass PDFs and HI power spectra. Fig. 3 shows the HI mass PDFs as well as the mean power spectrum and the standard deviation for $$1000$$ 
simulation data subcube projections (dotted lines) and the same number of HIGlow-generated samples (solid lines). The HI mass PDFs of the 
generated samples closely follow the target distribution, especially for HI masses below $$m_{\text{HI}} \approx 10^{5} \ M_{\odot}/h$$. In 
the range $$m_{\text{HI}} = 10^5-10^7 \ M_{\odot}/h$$, HIGlow captures the distribution less accurately, which is a result of the rarity 
of such high-mass pixels. For instance, $$m_{\text{HI}} = 10^6 \ M_{\odot}/h$$ pixels are $$6-7$$ orders of magnitude less likely than pixels 
with $$m_{\text{HI,peak}} \approx 20 \ M_{\odot}/h$$. The PDF bump around this peak value broadly corresponds to the Ly$$\alpha$$ forest in 
the post-reionization era [(Zamudio et al. 2019)](https://ui.adsabs.harvard.edu/abs/2019arXiv190412846Z).

Recall that we sigmoid-normalise the data before training HIGlow. The power spectra of Fig. 3 are 
also shown in sigmoid space since the trends with axion mass $m$ are more clear. We find that the target power spectra are reproduced 
with high fidelity, in particular the mean and standard deviation. The sigmoid-normalized power spectra exhibit the opposite trend with 
axion mass compared to the 3D non-sigmoid-normalized power spectra, see e.g. [Carucci et al. (2015)](https://ui.adsabs.harvard.edu/abs/2015JCAP...07..047C/abstract). 
We have checked and find that while the projection effect reduces the relative difference between cosmologies as reflected in 
2D vs 3D power spectra, the sigmoid normalization *reverses* the trend. 

In the evaluation of HIGlow, a conditional generative model, testing its capability to generate diverse samples spanning the entire 
latent space of axion masses is crucial. We test this functionality by choosing a new axion mass of $$m = 3\times 10^{-22}$$ eV, unexplored 
by the simulations, and generating $$1000$$ random images with HIGlow (see Fig. 2). Note that (unlike for CDM and the other three axion masses) 
we only show the HIGlow generated data for $$m = 3\times 10^{-22}$$ eV, as the corresponding simulation data does not exist for this mass. 
The statistics of the synthetic cosmology are shown in Fig. 3, exhibiting a striking resemblance to the anticipated outcome. Falling in 
between the curves corresponding to $$m = 10^{-22}$$ eV and $$m = 7 \times 10^{-22}$$ eV, the generated distribution effectively showcases the 
interpolation prowess in latent space. While a direct comparison to actual simulations at $$m = 3 \times 10^{-22}$$ eV would be needed for a 
more definitive test, the achieved success can be attributed to the monotonic albeit nonlinear influence of the axion mass $$m$$ on the 
distribution of HI.

| <img src="/assets/images/imapping/stats_sigmoid.png" width="450" height="950"> |
|:--:| 
| *Fig. 3: Statistical properties of simulation data (dotted lines) and HIGlow-generated HI samples (solid lines) at $$z=4.94$$ in CDM and cFDM cosmologies. We show HI mass PDFs (top panel), the median of 2D power spectra among $$1000$$ random samples (middle panel) and their standard deviation (bottom panel). In cyan, we add the results for a conditional axion mass of $$m = 3\times 10^{-22}$$ eV (see Fig. 2). This case does not have corresponding simulation data. The Nyquist frequency $$k_{\text{Ny}} = \pi N^{1/3} / L_{\text{box}}$$ is shown as a vertical line.* |


## Overall HI Abundance

## HI Power Spectrum and Bias

## HI Column Density Distributions

## DLA Cross-Sections

## Mock Radio Maps For SKA-Low

## Discussion