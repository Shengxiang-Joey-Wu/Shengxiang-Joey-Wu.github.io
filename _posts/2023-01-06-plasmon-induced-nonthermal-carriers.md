---
title: 'Plasmon Induced Nonthermal Carriers'
date: 2023-01-06
permalink: /posts/2023/01/plasmon-induced-nonthermal-carriers/
tags:
  - Plasmonics
  - Nonthermal Carriers
---

In the previous [blog](https://shengxiangwuplasmonic.github.io/posts/2022/09/what-is-plasmonic-nanostructure/), I mentioned that the non-radiative damping of surface plasmon was historically viewed as losses in the field of nanophotonics,<sup>1</sup> however, it is now a popular topic in the community of photocatalysis and photochemistry community since people realized that the 'losses', if managed properly, can be turned into advantages to drive (uphill) chemical reactions and even demonstrate certain bond selectivity that is not accessible by thermal means. 

The advantages are associated with energetic nonthermal or hot carriers that are generated after the non-radiative damping of surface plasmons, therefore it would be nice if one can predict the energy distribution of nonthermal carriers for given plasmonic nanoparticles. Indeed, there are multiple ways to perform such a calculation from free-electron-like algorithms<sup>2, 3</sup> to more rigorous treatments based on density functional theory (DFT).<sup>4, 5</sup> 

During my Ph.D. study and postdoctoral work, I have followed [ref. 2](https://pubs.acs.org/doi/10.1021/nn502445f) to calculate the energy profile of nonthermal carriers and then apply it to model the tunneling current<sup>6</sup> and photocatalytic performance.<sup>7</sup> It turns out that the approach used here could also be used as an extracurricular activity for first-year graduate students or senior undergraduates to strengthen the understanding of quantum chemistry. That being said, the replication of the major result of ref. 2 can be performed by combining the basic ideas of quantum chemistry and entry level of electromagnetics. Let's get started!

Preliminary Knowledge
======
**The Fermi-Golden Rule**
"In quantum physics, Fermi's golden rule is a formula that describes the transition rate (the probability of a transition per unit time) from one energy eigenstate of a quantum system to a group of energy eigenstates in a continuum, as a result of a weak perturbation" — Wikipedia.

[The Fermi-Golden rule](https://en.wikipedia.org/wiki/Fermi%27s_golden_rule) is the tool that we will use to analyze our problem, because we are interested in the transition probability of exciting an electron (hole), after a non-radiative decay of excited plasmon, from its initial state to possible final states. Therefore, before I throw you into a math puzzle, let me walk you through the fundamentals of the Fermi-Golden rule. (You may find derivation of the Fermi-Golden rule in many textbooks and online materials.)

It is essential a perturbation problem, let's for now assume the perturbation is from the electromagnetic filed of light (we will consider the effect of localized surface plasmon later), then the Hamiltonian of the system can be written as
$$H=H_0+H'$$

**References**
1. Khurgin, J. B. How to deal with the loss in plasmonics and metamaterials. *Nat Nanotechnol* **2015**, *10* (1), 2-6.
2. Manjavacas, A.; Liu, J. G.; Kulkarni, V.; Nordlander, P. Plasmon-Induced Hot Carriers in Metallic Nanoparticles. *ACS Nano* **2014**, *8* (8), 7630-7638.
3. Govorov, A. O.; Zhang, H.; Gun’ko, Y. K. Theory of Photoinjection of Hot Plasmonic Carriers from Metal Nanostructures into Semiconductors and Surface Molecules. *The Journal of Physical Chemistry C* **2013**, *117* (32), 16616-16631.
4. Sundararaman, R.; Narang, P.; Jermyn, A. S.; Goddard Iii, W. A.; Atwater, H. A. Theoretical predictions for hot-carrier generation from surface plasmon decay. *Nature Communications* **2014**, *5* (1), 5788.
5. Brown, A. M.; Sundararaman, R.; Narang, P.; Goddard, W. A., 3rd; Atwater, H. A. Nonradiative Plasmon Decay and Hot Carrier Dynamics: Effects of Phonons, Surfaces, and Geometry. *ACS Nano* **2016**, *10* (1), 957-966.
6. Wu, S.; Sheldon, M. T. Optical Power Conversion via Tunneling of Plasmonic Hot Carriers. *ACS Photonics* **2018**, *5* (6), 2516-2523.
7. Wu, S.; Chen, Y.; Gao, S. Plasmonic Photocatalysis with Nonthermalized Hot Carriers. *Physical Review Letters* **2022**, *129* (8), 086801.


