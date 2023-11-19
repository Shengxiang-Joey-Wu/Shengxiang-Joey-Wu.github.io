---
title: 'Numerical Modeling of Mie Scattering'
date: 2023-07-01
permalink: /posts/2023/07/numerical_modeling-of-mie-scattering/
excerpt: <img src="http://ShengxiangWuPlasmonic.github.io/images/blogImages/nmoms_TOC.jpg" width="719">
tags:
  - COMSOL Multiphysics
  - Finite Element Method
  - Finite-Difference Time-Domain Method
---

After I chose plasmonic nanoparticles (NPs) as my research field back in 2015, the first thing my advisor asked me to do was to reproduce the Mie scattering of gold NPs using Lumerical FDTD, a numerical solver developed by Lumerical Inc., which was acquired by Ansys in the year (2020) of my graduation. It was the first time I realized the power of modeling or simulation. Since then I have enjoyed comparing things, e.g., comparing theory with experiment, comparing different theories or methods, etc. Now I have been an experienced user of Lumerical FDTD (sorry Ansys, I still prefer to call it Lumerical FDTD) for more than 7 years. I have also been modeling nanophotonics problems with COMSOL Multiphysics, another popular numerical solver, for a long time, I still think it is a great exercise to look at this problem, namely, Mie scattering of plasmonic nanoparticles, the phenomenon that makes plasmonic NPs colorful and interesting in nanophotonics and photocatalytic domains. In this blog, I will walk you through the modeling process and we will compare our modeling result with the analytical solution - Mie theory.

Mie theory
=====

Mie theory is an exact analytic solution to Maxwell's equations for spheres with an arbitrary size and thus can be used to calculate the optical spectra, which essentially is an electromagnetic problem, of spherical particles, given that the dielectric constants of the particle and the environment are known. Rather than go through the development and derivation of Mie theory, which I believe deserves another blog, let's take its solution for granted for now and keep in mind that it is an analytical approach.

The general expression for the scattering and extinction cross sections from Mie theory are 

$$\sigma_\mathrm{sca}=\frac{2\pi R^2}{x^2}\sum_{n=1}^\infty(2n+1){|a_n|^2+|b_n|^2},$$

$$\sigma_\mathrm{ext}=\frac{2\pi R^2}{x^2}\sum_{n=1}^\infty(2n+1)Re[a_n+b_n],$$

where $x=2\pi Rn_\mathrm{m}/\lambda$, $n_\mathrm{m}$ is the refractive index of the medium, $R$ is the radius of the particle, and the absorption cross-section is given by $\sigma_\mathrm{abs}=\sigma_{ext}-\sigma_{sca}$. The $a_n$ and $b_n$ factors are given by

$$a_n=\frac{\psi'(mx)\psi_n(x)-m\psi_n(mx)\psi_n'(x)}{\psi'_n(mx)\zeta_n(x)-m\psi_n(mx)\zeta'_n(x)},$$

$$b_n=\frac{m\psi'_n(mx)\psi_n(x)-\psi_n(mx)\psi'_n(x)}{m\psi'_n(mx)\zeta_n(x)-\psi_n(mx)\zeta'_n(x)},$$

where $\psi_n(z)=(\pi z/2)^{1/2}\times J_{n+1/2}(z)$, $\zeta_n(z)=(\pi z/2)^{1/2}\times(J_{n+1/2}(z)-iY_{n+1/2}(z))$ and $m=n_p/n_m$, where $n_p$ is the refractive index of the particle.The different terms in eqs 1 and 2 correspond to the dipole ($n=1$), quadrupole ($n=2$), and so on.
