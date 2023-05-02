---
layout: page
title: Axions
katex: True
---

# QCD Axions

The mass of the classic QCD axion is not known with certainty, and it is one of the key properties that experimental efforts are attempting to determine. 
The mass of the axion is expected to be very light, with a range of possible values from as low as 1 micro-electronvolt (μeV) to as high as several milli-electronvolts (meV).

The exact value of the axion mass depends on the details of the Peccei-Quinn (PQ) mechanism and the energy scale at which the symmetry is broken. 
There are also different theoretical models that predict different values of the axion mass.

Experimental searches for the QCD axion are typically designed to target a specific mass range based on theoretical predictions. 
For example, the Axion Dark Matter eXperiment (ADMX) is focused on searching for axions with a mass in the range of 1 to 10 μeV. 
Other experiments, such as the Haloscope At Yale Sensitive to Axion Cold Dark Matter (HAYSTAC), the Magnetized Disc and Mirror Axion experiment (MADMAX), 
the CAPP Ultra-Low Temperature Axion Search in Korea (CULTASK), and the Cosmic Axion Spin Precession Experiment (CASPEr), are searching for axions 
with higher masses in the (sub-)meV range.

Despite decades of effort, the mass of the axion remains an open question, and further experimental searches will be necessary to determine its properties.

The axion field after PQ symmetry breaking (post-inflation) acts as a cold dark matter (CDM) condensate, and is thus a promising CDM candidate.

# Ultra-Light Axion Dark Matter

Another cold dark matter candidate are ultra-light axions (ULAs). ULAs are a class of axion particles that have masses in the range of 
about $$10^{-26}$$ to $$10^{-16}$$ eV. These axions are often referred to as "fuzzy" dark matter because their very low mass gives them a 
wavelength that is comparable to the size of small galaxies (kpc scales), which could lead to interesting effects on galactic structure.

One of the main motivations for studying ULAs is their potential impact on the structure of galaxies. Because their wavelength is 
comparable to the size of small galaxies, ULAs could exhibit wave-like behavior, forming a Bose-Einstein condensate (BEC) that would 
affect the distribution of matter in galaxies. This could potentially solve some of the outstanding problems in our understanding of 
galactic structure, such as the "cusp-core" problem and the "too big to fail" problem.

Search for the effects of ULAs on astrophysical phenomena has been an ongoing effort for years. Since the presence of ULAs affects 
the large-scale structure of galaxies, constraints can be put on the cosmological abundance of ULAs. In addition, the polarization of 
the cosmic microwave background radiation (CMB) is sensitive to ULAs and is being searched for by experiments like the Polarization of 
Background Radiation (POLARBEAR) experiment.

# Constraints
Experimental observations provide increasingly stringent bounds on the admissible mass ranges of FDM, see [Dome et al 2022](https://arxiv.org/pdf/2208.03827.pdf). In that work, we provide a non-exhaustive list of recent constraints ordered by publication date, which we also show below:

| ![Constraints](/assets/images/MassConstraints.png) | 
|:--:| 
| *Fig. 1: Recent particle mass constraints for warm dark matter (WDM) / FDM from astrophysical observations in the FDM window of $$10^{-26}$$ eV $$<m<10^{-16}$$ eV. The red shading indicates a disfavored parameter space, though not necessarily a $$2\sigma$$-constraint. The orange shading indicates forecasts for future observatories. UFDs = ultra-faint dwarf galaxies; SMBHs = supermassive black holes.* |

While the density profiles in the central regions of dwarf spheroidals can be explained with a FDM soliton core potential provided that 
$$m_a \le 1.1 \times 10^{-22}$$ eV [(Marsh & Pop 2015)](https://arxiv.org/abs/1502.03456), Ly-α observations find a lower 
bound $$m_a \ge 3.8 \times 10^{-21}$$ eV to have enough power on Mpc-scales 
in the Ly-α forest [(Irsic et al 2017)](https://arxiv.org/abs/1703.04683), constituting a Catch-22 problem. 
Recently, [Safarzadeh & Spergel 2020](https://arxiv.org/abs/1906.11848) showed that a pure FDM cosmology is inconsistent with dwarf spheroidals across the
entire parameter space by at least 3σ. More sophisticated models of
reionisation are needed though to make some of these observational
constraints more reliable: For instance, most forest analyses assume
that the frequency-averaged amplitude of the ionising background J
in the neutral hydrogen density $$n_{\text{HI}} \propto (1+\delta b)^2/(T^{0.7}J)$$ has negligible
spatial fluctuations [(Hui et al. 2017)](https://arxiv.org/abs/1610.08297). Some FDM constraints might also be biased due to poor star formation modelling.

# Impact on High-Redshift Large-Scale Structure

The high-$$z$$ large-scale structure (LSS) refers to the distribution of matter on the largest scales, spanning billions of light years. The *cosmic web* is a 
prominent feature of the large scale structure, consisting of a vast network of interconnected filaments and voids that stretch across the universe.
It is composed of dark matter and gas, which provide the scaffolding for the visible matter, such as stars and galaxies, to cluster and grow. The 
filaments of the cosmic web are the densest regions of matter, where galaxies and clusters of galaxies are found. These filaments are separated by 
vast, low-density voids, which are essentially empty regions of space. Nodes, knots, or virialised halos, form the smallest building block of the LSS. 

At high redshift, the Universe evolves mostly linearly, i.e. linear relativistic (or Newtonian) perturbation theory (PT) still provides an accurate 
description of gravitational collapse in an expanding Universe. When applying linear PT to a Gaussian field, which provides an accurate description of 
primordial density fluctuations in the early Universe, one finds that different wavelength modes do not couple; they evolve independently. Since FDM on 
large scales (including halo scales) is most manifest in an effective small-scale cutoff of the primordial density fluctuations, i.e. affecting 
small-scale modes, FDM imprints at high-$$z$$ are especially pronounced.

In [Dome et al 2022](https://arxiv.org/pdf/2208.03827.pdf), we quantify FDM imprints on the internal properties of halos by analysing a suite of $$N$$-body simulations, run for both CDM and multiple FDM models.

## Halo Density profiles

Halo density profiles are well approximated by the Einasto 
profile [(Einasto 1965)](https://ui.adsabs.harvard.edu/abs/1965TrAlm...5...87E/abstract),

$$\ln\left(\frac{\rho_E(r)}{\rho_{-2}}\right) = -\frac{2}{\alpha}\left[\left(\frac{r}{r_{-2}}\right)^{\alpha}-1\right].$$

which has three parameters: $$\alpha$$, the characteristic or scale radius $$r_s \equiv r_{-2}$$ at which the logarithmic slope has the 
isothermal value of $$-2$$, i.e. $$\mathrm{d} \ln{\rho} / \mathrm{d} \ln r|_{r_{-2}} = -2$$, and the density at the scale radius $$\rho_{-2}$$.

A useful quantity to keep in mind is the concentration of halos, defined as 

$$c = \frac{R_{200}}{r_{-2}},$$

i.e. the ratio of $$R_{200}$$ to that of the scale radius $$r_{-2}$$. As discussed by NFW 
[(Navarro et al 1996)](https://ui.adsabs.harvard.edu/abs/1996ApJ...462..563N/abstract)for the case of CDM, 
$$c$$ and $$M_{200}$$ do not take on arbitrary values, but correlate in a way that reflects the mass-dependence of halo formation 
times [(Bullock et al 2001)](https://ui.adsabs.harvard.edu/abs/2001MNRAS.321..559B/abstract). Earlier 
assembly corresponds to higher characteristic densities, reflecting the larger background density at that epoch. The $$c-M_{200}$$ relation
is shown below.

| <img src="/assets/images/cVersusM.png" width="400" height="850"> | *Fig. 2: Concentration-mass relation $$c(M,z)$$ in different cosmologies, for $$N$$-body, $$1024^3$$ resolution, $$L_{\text{box}} = 40$$ cMpc$$/h$$ runs at redshift $$z=4.38$$. We compare the CDM halos (blue) with cFDM halos for particle mass $$m=2\times 10^{-21}$$ eV (top), $$m=7\times 10^{-22}$$ eV (middle) and $$m=10^{-22}$$ eV (bottom). Square markers indicate median concentrations obtained from Einasto best-fits while the color of each hexbin is proportional to the number of halos whose Einasto concentration falls therein. "LB 16, CDM" and "LB 16, cFDM" show an analytical model prediction from [Ludlow et al 2016](https://arxiv.org/abs/1601.02624) for model parameters $$f=0.02$$ and $$C=650$$.* |
|:--:| 

[Ludlow 2014](https://academic.oup.com/mnras/article/441/1/378/977251) showed that the concentration of a CDM halo can be inferred 
from the critical density of the Universe at a characteristic time along its mass accretion history. The insight was used to construct an 
analytic model for the mass-concentration-redshift relation $$c(M,z)$$ for CDM halos, reproducing the inferred relation from many CDM 
simulations. In [Ludlow et al 2016](https://arxiv.org/abs/1601.02624), the generalisation of the model has been introduced and applied to 
WDM, relying on the full "collapsed mass history" of a halo instead of its main progenitor. As such, the model is based on extended 
Press-Schechter theory, allowing to assess the dependence of halo concentrations on cosmological parameters and on the shape of the 
linear matter power spectrum alike. It is this model whose validity for cFDM and high redshifts we would like to comment on.

Fig. 2 shows parts of the $$c(M,z)$$ relation as inferred from the $$N$$-body, $$1024^3$$ resolution, $$L_{\text{box}} = 40$$ cMpc$$/h$$ runs 
at redshift $$z=4.38$$. Square markers indicate concentrations as obtained from Einasto best-fits in the respective mass bin, while the color of 
each hexbin is proportional to the number of halos whose concentration falls therein. The solid blue curve labelled "LB 16, CDM" is a broken power-law 
fitting formula for $$c(M,z)$$ in the Planck cosmology from [Ludlow et al 2016](https://arxiv.org/abs/1601.02624) (Eq. C1). At fixed redshift $$z$$, 
the concentrations of CDM halos decrease monotonically with increasing halo mass, reflecting the lower background density at the epoch of their 
formation. At fixed mass, concentrations $$c$$ decrease monotonically with increasing redshift (not shown), indicative of the redshift evolution 
of the reference density, also called the *pseudo-evolution* of mass [(Diemer et al 2013)](https://ui.adsabs.harvard.edu/abs/2013ApJ...766...25D/abstract).

For cFDM, the concentration-mass relation is non-monotonic. In solid red labelled "LB 16, cFDM", we add the model prediction from 
[Ludlow et al 2016](https://arxiv.org/abs/1601.02624). To maintain consistency, as input to the model we use linear FDM matter power spectra obtained with 
*AxionCamb* rather than the [Viel et al 2005](https://arxiv.org/abs/astro-ph/0501562) parametrisation suitable for WDM. The model parameter $$f$$ that is used to define the halo collapse redshift is 
set to $$f = 0.02$$ while the proportionality factor $$C$$ relating mean inner halo densities to the critical density of the Universe at 
the collapse redshift is set to $$C = 650$$. We find that their model slightly overpredicts the cFDM concentrations at the small-mass end, 
while performing better for higher masses. At given $$z$$, concentrations peak at around two orders of magnitude above the half-mode mass 
scale $$M_{1/2}$$, with concentrations declining above and below this *peak mass scale* $$M_{\text{peak}} \sim 100 \times M_{1/2}$$. This is a 
known result which has also been described by e.g. [Bose et al 2015](https://arxiv.org/abs/1507.01998). However, both the latter work and that of 
[Ludlow et al 2016](https://arxiv.org/abs/1601.02624) focus on WDM simulations at low redshifts of $$z\leq 3$$ and equivalent cFDM 
particle masses of $$3.3\times 10^{-21}$$ eV and $$4.5\times 10^{-22}$$ eV. We extend the result to cFDM of lower particle mass 
of $$m = 10^{-22}$$ eV and to redshifts in the range $$3.4 \leq z \leq 6.3$$, beyond which 
our halo catalogues become too sparse and noisy to make statistically robust conclusions. We concede that for the $$m = 1 \times 10^{-22}$$ eV 
run (lower panel), our lack of high-mass halos makes the extrapolation towards $$M_{\text{peak}}$$ only tentative.

As in WDM, the non-monotonicity of $$c(M,z)$$ is due to the suppression of gravitational collapse below the half-mode scale, 
breaking the scale-invariance of the assembly process. It imprints a preferred scale on the mass accretion histories. 
While [Ludlow et al 2016](https://arxiv.org/abs/1601.02624) apply their model of the $$c(M,z)$$ relation to WDM, here we show 
that it also fares well for cFDM simulations with initial conditions based on *AxionCamb*, reproducing the non-monotonicity 
and even the constancy of $$M_{\text{peak}}$$ with cosmic time.