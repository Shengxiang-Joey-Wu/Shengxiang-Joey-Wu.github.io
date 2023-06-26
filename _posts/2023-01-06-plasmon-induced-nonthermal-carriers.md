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

$$H=H_0+H',$$

where $H_0$ is the unperturbed Hamiltonian and $H'$ represents perturbation. Let's say $H_0$ satisfied the time-dependent $\mathrm{Schr\ddot{o}dinger}$ equation (TDSE):

$$i\hbar\frac{\partial\Psi_0}{\partial t}=H_0\Psi_0,$$

where the wavefunction $\Psi_0$ has the generic form:

$$\Psi_0=\psi_0(\mathbf{r})e^{-iE_0t/\hbar},$$

Since the Hamiltonian (Energy) operator is a Hermitian operator, its eigenfunctions shall form a complete set. Let's use $|u\rangle$ represents the eigenfunctions of $H_0$, that is, $|u\rangle=\{u_1,u_2,\dots,u_n\}$. Then since any wavefunctions can be represented as the linear combination of the eigenfunctions (if these eigenfunctions form a complete set), eq. 3 can be written more generally as

$$\Psi_0=\sum_na_n^0u_n^0e^{-iE_n^0t/\hbar},$$

The subscript and suerscript $0$ denotes that it is evaluated at $t=0$ (no perturbation).
The unperturbed state described by $H_0$ has a set of energy eigenvalues such that

$$H_0u_n=E_nu_n,$$

By comparing eq. 3 and eq. 4, it is easy (hopefully for you as well) to tell that $\psi_0(\mathbf{r})=\sum_na_n^0u_n^0$ (a wavefunction can be described as a linear combination of complete orthonormal set $|u\rangle$). Note that the expansion coefficients $a_n^0$ are independent of time.

Suppose now we have a state described by wavefunction $\Psi$, and we are interested in how this wavefunction evolves (after the perturbation $H'$). We then put the wavefunction $\Psi$ in eq. 1 and use the TDSE

$$H\Psi=i\hbar\frac{\partial\Psi}{\partial t}=(H_0+H')\Psi,$$

and

$$\Psi=\sum_na_n(t)u_n^0e^{-iE_n^0t/\hbar},$$

Note that now the prefactors $a_n(t)$ depend on time.
Substituting eq. 7 into eq. 6, multiplying by the complex conjugate $u_s^{0*}$ and using the orthonormality of the wave functions,


$$\frac{\mathrm{d}a_s}{\mathrm{d}t}=\frac{-i}{\hbar}\sum_na_n(t)H_{sn}'\mathrm{e}^{i(E_s^0-E_n^0)t/\hbar},$$

where

$$H_{sn}'=\int u_s^{0*}H'u_n^0\mathrm{d}\tau,$$


The $\int\mathrm{d}\tau$ denotes integration over the full range of all the coordinates of a system.

For a small perturbation, the time variation of $a_n(t)$ is slow, then $a_n(t)\cong a_n(0)$ and

$$a_s(t)-a_s(0)\cong\frac{-i}{\hbar}\sum_na_n(0)\int_0^tH_{sn}'(t')e^{i\omega_{sn}t'}\mathrm{d}t',$$

where 

$$\hbar\omega_{sn}=E_s^0-E_n^0,$$

If, for simplicity, we consider the special case for which the system is in state $n$ at $t=0$. Then $a_n(0)=1$ and all other $a_n(t)=0$. Then

$$a_s(t)=\frac{-i}{\hbar}\int_0^tH'_{sn}(t')e^{i\omega_{sn}t'}\mathrm{d}t'$$

The eq. 12 just showed that $H'(t)$ can induce transitions from state $n$ to other states ($s\neq n$).


**References**
1. Khurgin, J. B. How to deal with the loss in plasmonics and metamaterials. *Nat Nanotechnol* **2015**, *10* (1), 2-6.
2. Manjavacas, A.; Liu, J. G.; Kulkarni, V.; Nordlander, P. Plasmon-Induced Hot Carriers in Metallic Nanoparticles. *ACS Nano* **2014**, *8* (8), 7630-7638.
3. Govorov, A. O.; Zhang, H.; Gun’ko, Y. K. Theory of Photoinjection of Hot Plasmonic Carriers from Metal Nanostructures into Semiconductors and Surface Molecules. *The Journal of Physical Chemistry C* **2013**, *117* (32), 16616-16631.
4. Sundararaman, R.; Narang, P.; Jermyn, A. S.; Goddard Iii, W. A.; Atwater, H. A. Theoretical predictions for hot-carrier generation from surface plasmon decay. *Nature Communications* **2014**, *5* (1), 5788.
5. Brown, A. M.; Sundararaman, R.; Narang, P.; Goddard, W. A., 3rd; Atwater, H. A. Nonradiative Plasmon Decay and Hot Carrier Dynamics: Effects of Phonons, Surfaces, and Geometry. *ACS Nano* **2016**, *10* (1), 957-966.
6. Wu, S.; Sheldon, M. T. Optical Power Conversion via Tunneling of Plasmonic Hot Carriers. *ACS Photonics* **2018**, *5* (6), 2516-2523.
7. Wu, S.; Chen, Y.; Gao, S. Plasmonic Photocatalysis with Nonthermalized Hot Carriers. *Physical Review Letters* **2022**, *129* (8), 086801.


