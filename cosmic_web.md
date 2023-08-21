---
layout: page
title: Cosmic Web
katex: True
---

On scales of $$1-100$$ Mpc the matter distribution of the Universe forms a weblike pattern of voids separated by walls, 
filaments and nodes - the *cosmic web* [(Bond et al. 1996)](https://www.nature.com/articles/380603a0). The most prominent 
features of the cosmic web are filaments, and beyond the well-known Pisces-Perseus chain 
[(Giovanelli & Haynes 1985)](https://ui.adsabs.harvard.edu/abs/1985ApJ...292..404G/abstract) in the local Universe, entire filament 
inventories have been catalogued [(Tempel et al. 2014)](https://ui.adsabs.harvard.edu/abs/2014MNRAS.438.3465T/abstract). The largest 
filaments act as highways of the Universe, channelling dark matter, gas and galaxies into the higher density node 
regions. The nodes contain the highest density of galaxy clusters and superclusters such as the Great Attractor [(Lynden-Bell
et al. 1988)](https://ui.adsabs.harvard.edu/abs/1988ApJ...326...19L/abstract), the Shapley concentration 
[(Ragone et al. 2006)](https://ui.adsabs.harvard.edu/abs/2006A%26A...445..819R/abstract) or the Vela 
supercluster [(Kraan-Korteweg et al. 2017)](https://ui.adsabs.harvard.edu/abs/2017MNRAS.466L..29K).

The 2D components of the cosmic web, sheet-like membranes, are more difficult to detect in the spatial mass distribution 
traced by galaxies due to their lower surface density. The spatial structure outlined by galaxy clusters, however, does feature flattened 
supercluster configurations coined great walls, the most outstanding of which are the CfA Great Wall 
[(Geller & Huchra 1989)](https://ui.adsabs.harvard.edu/abs/1989Sci...246..897G/abstract), the 
Sloan Great Wall [(Gott et al. 2005)](https://ui.adsabs.harvard.edu/abs/2005ApJ...624..463G/abstract), the BOSS Great Wall 
[(Lietzen et al. 2016)](https://www.aanda.org/articles/aa/full_html/2016/04/aa28261-16/aa28261-16.html) and the supergalactic plane 
[(Lahav et al. 2000)](https://academic.oup.com/mnras/article/312/1/166/984983). Finally, large void regions are prominent features 
in redshift surveys as they are practically devoid of any galaxy. Recent studies 
[(Leclercq et al. 2015)](https://iopscience.iop.org/article/10.1088/1475-7516/2015/03/047) provide 
increasingly refined maps and catalogues of the void population in the local Universe. Out of all known voids, the Local 
Void with a diameter of 30 Mpc is closest to the Milky Way.

At high redshift, the Universe evolves mostly linearly, i.e. linear relativistic (or Newtonian) perturbation theory (PT) still provides an accurate 
description of gravitational collapse in an expanding Universe. When applying linear PT to a Gaussian field, which provides an accurate description of 
primordial density fluctuations in the early Universe, one finds that different wavelength modes do not couple; they evolve independently. 
The cosmic web is still in the linear or quasi-linear phase of collapse. Since FDM on large scales (including halo scales) is most manifest in an 
effective small-scale cutoff of the primordial density fluctuations, i.e. affecting small-scale modes, FDM imprints on the cosmic web 
at high-$$z$$ are especially pronounced. These imprints are only observable via tracer fields, but in simulations we can 
predict the configuration and abundance of each morphological component in CDM and FDM.

On this page we show results for the cosmic web dissection of numerical CDM and FDM simulations into the four morphological components. For more details 
about the internal properties of halos embedded in the densest component (i.e. nodes) in CDM and FDM see [this page](halos.md).

## NEXUS Segmentation

Cosmic web detection algorithms can be categorised into graph- and percolation-based techniques 
[(Naidoo et al. 2022)](https://ui.adsabs.harvard.edu/abs/2022MNRAS.513.3596N), stochastic methods 
[(Stoica et al. 2010)](https://ui.adsabs.harvard.edu/abs/2010A%26A...510A..38S/abstract), topological methods 
[(Aragón-Calvo et al. 2010)](https://ui.adsabs.harvard.edu/abs/2010ApJ...723..364A) and Hessian-based approaches, see 
[Libeskind et al. (2017)](https://academic.oup.com/mnras/article/473/1/1195/4062204) for a comparison. Our focus in the following is on 
Hessian-based approaches which exploit morphological information in the gradient (or Hessian) of the density, tidal or velocity shear fields.
Most of the Hessian-based formalisms are defined on one particular smoothing scale for the field involved 
[(Bond et al. 2010)](https://ui.adsabs.harvard.edu/abs/2010MNRAS.409..156B), but explicit multiscale versions have also been
developed, including [(Aragón-Calvo & Jones 2007)](https://www.aanda.org/articles/aa/abs/2007/40/aa7880-07/aa7880-07.html).

In this work we use NEXUS+. NEXUS+ is likewise a morphological multiscale approach based on the density field Hessian. By
log-smoothing the density field over a range of spatial filter sizes $$R_n \in (R_0, ..., R_N)$$ and maximising over the signatures in this so-called
scale-space, it detects at which scales and locations the various morphological signatures are most prominent. The six steps of the algorithm 
along with our implementation choices are as follows.

1. Applying a log-Gaussian filter of width $$R_n$$ to the input field. If the input field is continuous and denoted by $$f(\vec{x})$$, 
   smoothing the log-field $$g = \log_{10} f$$ amounts to a simple multiplication with the Gaussian exponential in Fourier space:

   $$g_{R_n}(\vec{x}) = \int_{\mathbb{R}^3} \frac{d^3\vec{k}}{(2\pi)^3}e^{-\vec{k}^2\frac{R_n^2}{2}}\hat{g}(\vec{k})e^{i\vec{k}\vec{x}}.$$

   This yields the NEXUS+ smoothed field $$f_{R_n}(\vec{x}) = C_{R_n}10^{g_{R_n}(\vec{x})}$$ by exponentiation, where $$C_{R_n}$$ assures 
   the mean of the input field is the same before and after filtering.

2. Computing Hessian eigenvalues. The Fourier transform of the Hessian $$H_{ij,R_n}(\vec{x})=R_n^2\frac{\partial^2 f_{R_n}(\vec{x})}{\partial x_i \partial x_j}$$ reads

   $$H_{ij,R_n}(\vec{k})=-k_ik_jR_n^2\hat{f}_{R_n}(\vec{k}).$$

3. Assigning to each point a cluster, filament and wall signature. The three eigenvalues $$\lambda_1 \leq \lambda_2 \leq \lambda_3$$ of the 
   Hessian $$H_{ij,R_n}(\vec{x})$$ can be combined into a shape strength as

   $$\mathcal{I}_{R_n} = 
   \begin{cases}
   	\ \big|\frac{\lambda_3}{\lambda_1} \big| & \text{node} \\ 
   	\ \big|\frac{\lambda_2}{\lambda_1} \big| \Theta\left(1-\big|\frac{\lambda_3}{\lambda_1} \big|\right) & \text{filament}\\
   	\ \Theta\left(1-\big|\frac{\lambda_2}{\lambda_1} \big|\right) \Theta\left(1-\big|\frac{\lambda_3}{\lambda_1} \big|\right) & \text{wall},
   \end{cases}$$

   where we use the notation $$\Theta(x) = x\theta(x)$$ for clarity, with $$\theta(x)$$ the Heaviside step function $$\theta(x) = 1$$ if $$x \geq 0$$, $$0$$ otherwise. 
   We thus obtain the cluster/filament/wall signature as:

   $$\mathcal{S}_{R_n} = \mathcal{I}_{R_n}\times
   \begin{cases}
   	\ |\lambda_3|\theta(-\lambda_1)\theta(-\lambda_2)\theta(-\lambda_3) & \text{node} \\ 
   	\ |\lambda_2|\theta(-\lambda_1)\theta(-\lambda_2) & \text{filament}\\
   	\ |\lambda_1|\theta(-\lambda_1) & \text{wall}.
   \end{cases}$$

   We multiply by $$|\lambda_i|$$ to distinguish between noise (small $$|\lambda_i|$$) and real signals (large $$|\lambda_i|$$) while the $$\theta(-\lambda_i)$$ 
   factors impose the necessary eigenvalue constraints.

4. Computing the environmental signature over a range of smoothing scales. We repeat steps 1-3 over a range of smoothing scales $$(R_0, R_1, ..., R_N)$$. 
   While NEXUS+ is a multi-scale approach, the hierarchy of smoothing scales is a user input. In view of computational feasibility, 
   we opt for relative $$\sqrt{2}$$-spacings following [Cautun et al. (2012)](https://academic.oup.com/mnras/article/429/2/1286/1038906), 
   i.e. $$R_n = (\sqrt{2})^nR_0$$, where $$R_0$$ is the smallest scale at which to expect to find structures. We comment 
   on $$R_0$$ and the discretization of $$f(\vec{x})$$ below while $$N$$ is chosen such that $$R_N$$ does not exceed $$4 \ h^{-1}$$Mpc. 
   At higher redshift of $$z>1$$, smaller values for $$R_N$$ would suffice.

5. Scale-space stacking. The scale-independent map is constructed by taking the maximum signature over all scales

   $$\mathcal{S}(\vec{x}) = \max_{\text{levels } n} \mathcal{S}_{R_n}(\vec{x}),$$

   which characterizes the degree to which each voxel $$\vec{x}$$ is part of a cluster, filament or wall.

6. Computing the detection threshold. As the last step, we impose physical criteria to determine the detection threshold corresponding to 
   valid environments. For nodes, the threshold signature $$\mathcal{S}_{c,\mathrm{cut}}$$ is found by requiring that at least half of the 
   connected regions are virialised according to Eq. \href{#formula}{foo}. This is in contrast to the original papers 
   [Cautun et al. (2012)](https://academic.oup.com/mnras/article/429/2/1286/1038906) and
   [Cautun et al. (2014)](https://academic.oup.com/mnras/article/441/4/2923/1213214), where the authors use a virialisation overdensity 
   of $$\Delta_{\text{vir}} = 370$$. To identify connected regions for each node signature floor $$\mathcal{S}_{c}$$, we label them based on a 
   $$1$$-connectivity neighbourhood condition. The value $$1$$ refers to the maximum number of orthogonal hops to consider a voxel a neighbour.

   Voxels that do not pass this threshold are assigned a node signature of zero. Voxels that do pass the threshold constitute genuine node 
   structures, and after setting the real-space density values at their location to the mean density of the Universe (rather than zero as in 
   [Cautun et al. (2012)](https://academic.oup.com/mnras/article/429/2/1286/1038906)), the slightly modified input field 
   $$\tilde{\delta}(\mathbf{x})$$ becomes the basis for the calculation of filament signatures $$\mathcal{S}_{f,R_n}(\mathbf{x})$$ in step 3. 
   The procedure is similar to the one for nodes, except that for filaments, the threshold signature is determined by calculating the 
   mass $$M_f(\mathcal{S}_f)$$ in filaments with a signature value larger or equal to $$\mathcal{S}_f$$ and maximizing the mass change with signature:

```math
:label: e_fw_det
\argmax_{\mathcal{S}_f} \ \bigg\lvert \frac{\mathrm{d}M_f^2}{\mathrm{d}\log \mathcal{S}_f}\bigg\rvert = \mathcal{S}_{f,\mathrm{cut}}.
```
   
   After identifying filaments and setting the real-space density values
   at their location to the mean density of the Universe, we identify
   walls using the same detection threshold {eq}`e_fw_det`. The remaining voxels are automatically identified 
   as voids, which thus constitute the complement to nodes, filaments and walls.

## Cosmic Web Statistics at High Redshift
