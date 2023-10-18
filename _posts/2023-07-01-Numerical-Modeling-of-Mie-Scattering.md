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

After I chose plasmonic nanoparticles (NPs) as my research field back in 2015, the first thing my advisor asked me to do was to reproduce the Mie scattering of gold NPs using Lumerical FDTD, a numerical solver developed by Lumerical Inc., which was acquired by Ansys in the year (2020) of my graduation. It was the first time I realized the power of modeling or simulation and since then I enjoyed comparing things, e.g., comparing theory with experiment, comparing different theories or methods, etc. Now I have been an experienced user of Lumerical FDTD (sorry Ansys, I still prefer to call it Lumerical FDTD) for more than 7 years and I have also been modeling nanophotonics problems with COMSOL Multiphysics, another popular numerical solver, for a long time, I still think it is a great exercise to look at this problem, namely, Mie scattering of plasmonic nanoparticles, the phenomenon that makes plasmonic NPs colorful and interesting in nanophotonics and photocatalytic domains. In this blog, I will walk you through the modeling process and we will compare our modeling result with the analytical solution - Mie theory.

Mie theory
=====
