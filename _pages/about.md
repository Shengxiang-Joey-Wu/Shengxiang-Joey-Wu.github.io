---
permalink: /
title: ""
excerpt: "About me"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

Howdy! Welcome to my academic website. My name is Shengxiang (Joey) Wu, and I would like to document my academic progress here and share some scientific notes on my [Blog Posts](https://shengxiangwuplasmonic.github.io/year-archive/). I name this website "Plasmonics for Clean Energy" because I truly believe and hope my interested research area - 'plasmonic nanostructures' can provide clean energy for the world and help our planet fighting against climate change.

Plasmonic Nanostructures
======
*What is plasmon?* This is the question I asked the first day I entered the graduate school as I just switched from Chemical Biology major. Many papers introduce plasmons as **the collective oscillation of electrons**. Yet not entirely satisfied to this definition because two questions are still not answered: 1) why there is a resonance present when illuminating plasmonic nanostructures? 2) why people always refer to noble metals (e.g., gold, silver) when talking about plasmonic nanostructures?, let's accept this definition and restrict our attention to noble metals for the time being. Alternative introduction to plasmonic nanoparticles and the answers to the two questions can be found in [Phys Rev Lett 2005, 95 (9), 095504.](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.95.095504).

<p align="center">
<img src="http://ShengxiangWuPlasmonic.github.io/images/Figure_1.jpg" width="500">
</p>  

Following the naive rationale, the oscillaltion of free electrons is simply due to the response of electrons (a negatively charged particle) to the alternating electric field of light (electromagnetic waves). This oscillation is usually occured at the metal/dielectric interface and if it is restricted to a nanostructure with well-defined shape, the localized surface plasmon (LSP) emerges. And we termed nanoparticles that support LSP the plasmonic nanostructures. 

Note: There is another type of plasmon, the surface plasmon polariton (SPP) that can propagate along the surface, which is important in nanophotonic applications such as waveguides. 

Localized Surface Plasmon Resonance (LSPR)
=====
If one illuminates a plasmonic nanosphere with varied wavelengths, one may found a peak in the absorption or scattering spectrum, which indicates a resonance (LSPR). The wavelength/frequency that this peak occurs is termed the surface plasmon resonance frequency. Now you can imagine why I am not satisfied with *plasmons are the collective oscillations of electrons*: oscillations do not necessarily yield a resonance. This insatisfactory is resolved if we view the plasmonic nanoparticle with its dielectric environment as [a nanoscaled LC-circuit](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.95.095504), then the LSPR emerges naturally and simiarily as in a LC-resonator. With this in mind, we can imagine that the electrons oscillate much stronger at plasmon resonance frequency compare to the out-of-resonance condition.

The surface plasmon resonance can be tailored easily by modifying the composiiton, size, shape, and the dielectric environment of the nanoparticle (see the extinction spectrum below). This makes plasmonic nanostructures extremely promising in various applications, such as sensing, photodetection, etc.

<p align="center">
<img src="http://ShengxiangWuPlasmonic.github.io/images/Figure_2.jpg" width="500">
</p>  

Damping of LSPR
=====
What happens after one excites the localized surface plasmon, especially at its LSPR? Of course we do not expect the oscillation of electrons to last forever as there are many ways for electrons to scatter off. It turns out that the LSP can undergo two major damping channels: the radiative damping (observed as light scattering) and the non-radiative damping (observed as absorption). In addition to these two channels, it is also found that LSP can dephase through scattering with adsorbded molecules or nearby semiconductors, and this damping channel is identified as the [Chemical Interface Damping](https://pubs.acs.org/doi/10.1021/acs.accounts.0c00872).

Specifically, I would like to narrow the focus to the non-radiative decay of surface plasmon, which was historically considered as 'loss'. While there are continuous effort to minimize this 'loss', it turns out that the non-radiative decay of surface plasmon may lead to energetic carriers that can be harvested in many fields, e.g., photodetection, photocatalysis, etc.

Dynamics of Plasmonic Nonthermal Carriers
=====
In fact, the photothermal heating is just the last stage of nonradiative decay of surface plasmon (absorption): there are early stages where the plasmonic energy is temporily stored in the electronic subsystem, rather than in lattice phonons. I prefer to term the carriers (electrons and holes) at the first stage immediately after nonradiative decay the **nonthermal carriers** (see [Blog Posts](https://shengxiangwuplasmonic.github.io/year-archive/) for calculation examples), as their energy distribution is not a Fermi-Dirac like distribution. That is saying, their energy profile cannot be described using a effective temperature. The nonthermal carriers are extremely short-lived (~100 fs) and they relax within the electronic subsystem through electron-electron scatterings, and these scatterings move the carriers to the second stage. On the second stage, the carriers still have greater energy compared with the phonons, but now their energy profile is Fermi-Dirac-like and thus can be described using an effective temperature $T_e$. Therefore, they are termed **hot carriers**. On the final stage (photothermal heating), the electrons are thermalized with phonons through electron-phonon scatterings (~ps to ns), and I call these carreiers **thermalized carriers**. 

<p align="center">
<img src="http://ShengxiangWuPlasmonic.github.io/images/Figure_3.jpg" width="500">
</p>  

I would like to note here that since both nonthermal carriers and hot carriers are more energetic than thermalized carriers, we may find in many literatures people (including me) use *hot carriers* to refer both types of carriers. My research interest now lies in utilizing plasmon-induced nonthermal and hot carriers to catalyze (electro)chemical reactions with high yield and selectivity. 

