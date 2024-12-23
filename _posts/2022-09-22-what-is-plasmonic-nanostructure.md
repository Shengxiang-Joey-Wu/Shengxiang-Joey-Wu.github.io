---
title: 'What is Plasmonic Nanostructure?'
date: 2022-09-22
permalink: /posts/2022/09/what-is-plasmonic-nanostructure/
excerpt: <img src="http://Shengxiang-Joey-Wu.github.io/images/blogImages/wipn_TOC.jpg" width="528">
tags:
  - Plasmonics
  - Nanostructure
---
Plasmonic Nanostructures
======
*What is a plasmon?* This is the question I asked the first day I entered graduate school as I had just switched from a *Chemistry* major. Many papers introduce plasmons as **the collective oscillation of electrons** as illustrated in Figure 1. Yet not entirely satisfied with this definition because two questions are still not answered: 1) why there is a resonance present when illuminating plasmonic nanostructures? 2) why do people always refer to noble metals (e.g., gold, silver) when talking about plasmonic nanostructures? let's accept this definition and restrict our attention to noble metals for the time being. An alternative introduction to plasmonic nanoparticles and the answers to the two questions can be found using equivalent circuit theory.<sup>[1](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.95.095504)</sup>

<p align="center">
<img src="http://Shengxiang-Joey-Wu.github.io/images/blogImages/wipn_Figure1.jpg" width="559">
</p>  

Following this naive rationale, the collective oscillation of free electrons is simply due to the response of electrons (a negatively charged particle) to the alternating electric field of light (electromagnetic waves). This oscillation occurred at the metal/dielectric interface and if it is restricted to a nanostructure with a well-defined shape, the localized surface plasmon (LSP) emerges. And we termed nanoparticles that support LSP the plasmonic nanostructures. 

Note: There is another type of plasmon (polariton), the surface plasmon polariton (SPP) that can propagate along the surface, which is important in nanophotonic applications such as waveguides. 

Localized Surface Plasmon Resonance (LSPR)
=====
If one excites a plasmonic nanosphere with broadband illumination, one may find a peak in the absorption or scattering spectrum, which indicates a resonance (LSPR). The wavelength/frequency that this peak occurs is termed the surface plasmon resonance frequency. Now you can imagine why I am not satisfied with *plasmons are the collective oscillations of electrons*: oscillations do not necessarily yield a resonance. This unsatisfactory is resolved if we view the plasmonic nanoparticle along with its dielectric environment as [a nanoscaled LC-circuit](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.95.095504), then the LSPR emerges naturally as in an LC-resonator. With this in mind, we can imagine that the electrons oscillate much stronger at plasmon resonance frequency compare to the out-of-resonance condition.

The surface plasmon resonance can be tailored easily by modifying the composition, size, shape, and dielectric environment (Figure 2). This makes plasmonic nanostructures extremely promising in various applications, such as sensing, photodetection, etc.

<p align="center">
<img src="http://Shengxiang-Joey-Wu.github.io/images/blogImages/wipn_Figure2.jpg" width="630">
</p>  

Damping of LSPR
=====
What happens after one excites the localized surface plasmon, especially at its LSPR? Of course, we do not expect the oscillation of electrons would last forever as there are many ways for electrons to scatter off. It turns out that the LSP can undergo two major damping channels: radiative damping (observed as light scattering) and non-radiative damping (observed as absorption). In addition to these two channels, it is also found that LSP can dephase through scattering with adsorbed molecules or adjacent semiconductors, and this damping channel is identified as chemical interface damping (CID).<sup>[2](https://pubs.acs.org/doi/10.1021/acs.accounts.0c00872)</sup>

Specifically, I would like to narrow the focus to the non-radiative decay of surface plasmon, which was historically considered a 'loss'. While there are continuous efforts to minimize this 'loss', it turns out that the non-radiative decay of surface plasmon may lead to energetic carriers that can be harvested in many fields, e.g., photodetection, photocatalysis, etc.

Dynamics of Plasmonic Nonthermal Carriers
=====
In fact, photothermal heating is just the last stage of the non-radiative decay of surface plasmon (absorption). There are early stages where the plasmonic energy is temporarily stored in the electronic subsystem, rather than in lattice phonons as shown in Figure 3.<sup>[3](https://www.annualreviews.org/doi/abs/10.1146/annurev-physchem-062422-014911)</sup> I prefer to term the carriers (electrons and holes) at the first stage immediately after non-radiative decay the **nonthermal carriers** (see [Blog Posts](https://shengxiang-joey-wu.github.io/year-archive/) for calculation examples), as their energy distribution is not a Fermi-Dirac like distribution. That being said, the energy profile of nonthermal carriers cannot be described using an effective temperature. The nonthermal carriers are extremely short-lived (~100 fs) and relax within the electronic subsystem through electron-electron scatterings, and these scatterings move the carriers to the second stage. In the second stage, the carriers still have greater energy compared with lattice phonons, but now their energy profile is Fermi-Dirac-like and thus can be described using an effective temperature $T_e$, and thus termed **hot carriers**. In the final stage (photothermal heating), the electrons are thermalized with phonons through electron-phonon scatterings (~ps to ns), and I call these carriers **thermalized carriers**. 

<p align="center">
<img src="http://Shengxiang-Joey-Wu.github.io/images/blogImages/wipn_Figure3.jpg" width="571">
</p>  

I would like to note here that since both nonthermal carriers and hot carriers are more energetic than thermalized carriers, we may find in many literatures where people (including me) use *hot carriers* and *nonthermal carriers* interchangeably. Part of my research interest lies in utilizing plasmon-induced nonthermal and hot carriers to catalyze (electro)chemical reactions with high yield and selectivity.

**References**
1.  Engheta, N.; Salandrino, A.; Alu, A. Circuit elements at optical frequencies: nanoinductors, nanocapacitors, and nanoresistors. *Phys Rev Lett* **2005**, *95* (9), 095504.
2.  Lee, S. A.; Link, S. Chemical Interface Damping of Surface Plasmon Resonances. *Acc Chem Res* **2021**, *54* (8), 1950-1960.
3.  Wu, S.; Sheldon, M. Mechanisms of Photothermalization in Plasmonic Nanostructures: Insights into the Steady State. *Annual Review of Physical Chemistry* **2023**, *74* (1), 521-545.
