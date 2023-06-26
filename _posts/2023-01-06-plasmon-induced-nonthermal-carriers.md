---
title: 'Plasmon Induced Nonthermal Carriers'
date: 2023-01-06
permalink: /posts/2023/01/plasmon-induced-nonthermal-carriers/
tags:
  - Plasmonics
  - Nonthermal Carriers
---

In the previous [blog](https://shengxiangwuplasmonic.github.io/posts/2022/09/what-is-plasmonic-nanostructure/), I mentioned that the non-radiative damping of surface plasmon was historically viewed as losses in the field of nanophotonics,<sup>1</sup> however, it is now a popular topic in the community of photocatalysis and photochemistry since people realized that the 'losses', if managed properly, can be turned into advantages to drive (uphill) chemical reactions and even demonstrate certain bond selectivity that is not accessible by thermal means. 

The advantages are associated with energetic nonthermal or hot carriers that are generated after the non-radiative damping of surface plasmons, therefore it would be nice if one can predict the energy distribution of nonthermal carriers for given plasmonic nanoparticles. Indeed, there are multiple ways to perform such a calculation from free-electron-like algorithms<sup>2, 3</sup> to more rigorous treatments based on density functional theory (DFT).<sup>4, 5</sup> 

During my Ph.D. study and postdoctoral work, I have followed [ref. 2](https://pubs.acs.org/doi/10.1021/nn502445f) to calculate the energy profile of nonthermal carriers and then apply it to model the tunneling current<sup>6</sup> and photocatalytic performance.<sup>7</sup> It turns out that the approach used here could also be used as an extracurricular activity for first-year graduate students or senior undergraduates to strengthen their understanding of quantum chemistry. That being said, the replication of the major result of ref. 2 can be performed by combining the basic ideas of quantum chemistry and entry-level electromagnetics. Let's get started!

Preliminary Knowledge
======

**The Fermi-Golden Rule**

"In quantum physics, Fermi's golden rule is a formula that describes the transition rate (the probability of a transition per unit time) from one energy eigenstate of a quantum system to a group of energy eigenstates in a continuum, as a result of a weak perturbation" — Wikipedia.

[The Fermi-Golden rule](https://en.wikipedia.org/wiki/Fermi%27s_golden_rule) is the tool that we will use to analyze our problem, because we are interested in the transition probability of exciting an electron (hole), after a non-radiative decay of excited plasmon, from its initial state to possible final states. Therefore, before I throw you into a math puzzle, let me walk you through the fundamentals of the Fermi-Golden rule. (You may find the derivation of the Fermi-Golden rule in many textbooks and online materials.)

It is essentially a perturbation problem, let's for now assume the perturbation is from the electromagnetic field of light (we will consider the effect of localized surface plasmon later), then the Hamiltonian of the system can be written as

$$H=H_0+H',$$

where $H_0$ is the unperturbed Hamiltonian and $H'$ represents perturbation. Let's say $H_0$ satisfied the time-dependent $\mathrm{Schr\ddot{o}dinger}$ equation (TDSE):

$$i\hbar\frac{\partial\Psi_0}{\partial t}=H_0\Psi_0,$$

where the wavefunction $\Psi_0$ has the generic form:

$$\Psi_0=\psi_0(\mathbf{r})e^{-iE_0t/\hbar},$$

Since the Hamiltonian (Energy) operator is a Hermitian operator, its eigenfunctions shall form a complete set. Let's use $\vert u\rangle$ represents the eigenfunctions of $H_0$, that is, $\vert u\rangle=\{u_1,u_2,\dots,u_n\}$. Then since any wavefunctions can be represented as the linear combination of the eigenfunctions (if these eigenfunctions form a complete set), eq. 3 can be written more generally as

$$\Psi_0=\sum_na_n^0u_n^0e^{-iE_n^0t/\hbar},$$

The subscript and superscript $0$ denote that it is evaluated at $t=0$ (no perturbation).
The unperturbed state described by $H_0$ has a set of energy eigenvalues such that

$$H_0u_n=E_nu_n,$$

By comparing eq. 3 and eq. 4, it is easy (hopefully for you as well) to tell that $\psi_0(\mathbf{r})=\sum_na_n^0u_n^0$ (a wavefunction can be described as a linear combination of complete orthonormal set $\vert u\rangle$). Note that the expansion coefficients $a_n^0$ are independent of time.

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

$$a_s(t)=\frac{-i}{\hbar}\int_0^tH'_{sn}(t')e^{i\omega_{sn}t'}\mathrm{d}t'\qquad\mathrm{for}\;s\neq n,$$

The eq. 12 just showed that $H'(t)$ can induce transitions from state $n$ to other states ($s\neq n$).

If $H'$ is independent of time,

$$a_s(t)=\frac{-i}{\hbar}H'_{sn}\int_0^te^{i\omega_{sn}t'}\mathrm{d}t'=-H_{sn}'\frac{(e^{i\omega_{sn}t}-1)}{\hbar\omega_{sn}},$$

Therefore,

$$\vert a_s(t)\vert^2=4\vert H'_{sn}\vert^2\sin^2(\frac{\omega_{sn}t}{2})/(\hbar^2\omega_{sn}^2),$$

For many techniques, the result of perturbation is a final state that places particle in the continuum, that is, a free particle. In this case, an explicit final state can be replaced by a density of final states. Such a density is defined as the number of energy levels per unit energy interval $\mathrm{d}E$. The *transition probability* $P(t)$ for discrete states is given as

$$P(t)=\sum_s|a_s(t)|^2=4|H_{sn}'|^2\sum\sin^2(\frac{\omega_{sn}t}{2})/(\hbar^2\omega_{sn}^2),$$

For a continuum, the summation is replaced by an integral so that

$$P(t)=4|H_{sn}'|^2\int_{-\infty}^\infty\rho(E_s)\sin^2(\omega_{sn}t/2)/(\hbar^2\omega_{sn}^2)\mathrm{d}\hbar\omega_{sn},$$

The major contribution to this integral occurs at $\omega_{sn}=0$, similar to a delta function. Hence, $\rho(E_s)\sim\rho(E_n)$. Furthermore, the integral in (1.16) is of the form $\int_{-\infty}^\infty\sin^2(\alpha x)/x^2\mathrm{d}x=\pi\alpha$, where $\alpha=\frac{t}{2\hbar}$.

Therefore, the integral reduces to

$$P(t)=4|H_{sn}'|^2\rho(E_n)(\frac{\pi t}{2\hbar}),$$

and the rate of transition $R=\mathrm{d}P(t)/\mathrm{d}t$ in units of $\mathrm{s^{-1}}$ is equal to 

$$R=\frac{2\pi}{\hbar}\rho(E_n)|H_{sn}'|^2$$

Eq. 18 is indeed the well-known Fermi-Golden rule.

Sometimes you may see the Fermi-Golden rule attached with a $\delta$ function, here we can demonstrate this process.
We can rewrite eq. 14 as 

$$|a_s(t)|^2=4|H'_{sn}|^2\sin^2(\frac{\omega_{sn}t}{2})/(\hbar^2\omega_{sn}^2)=\frac{|H_{sn}'|^2}{\hbar^2}t^2\frac{\sin^2(\omega_{sn}t/2)}{\omega_{sn}^2t^2/4}=\frac{|H_{sn}'|^2}{\hbar^2}t^2\mathrm{sinc}^2(\omega_{sn}t/2),$$

Since $\lim\limits_{x\rightarrow 0}\mathrm{sinc}(x)=1$, eq. 19 becomes

$$|a_s(t)|^2=\frac{|H_{sn}'|^2}{\hbar^2}t^2,$$

Thus, the short-time behavior is *quadratic* with time.

For the long time limit ($t\rightarrow\infty$), we also rewrite eq. 13 as 

$$\vert a_s(t)\vert^2=4\vert H'_{sn}\vert^2\sin^2(\frac{\omega_{sn}t}{2})/(\hbar^2\omega_{sn}^2)=4\vert H_{sn}'\vert^2\sin^2(\frac{\Delta Et}{2\hbar})/(\Delta E)^2,$$

Here, we've defined $\Delta E=E_s-E_n=\omega_{sn}\hbar$. Let us further define $D_t(\Delta E)\equiv4\sin^2(\frac{\Delta Et}{2\hbar})/(\Delta E)^2$, we plot $D_t(\Delta E)$ vs. $\Delta E$ to visualize its properties (Figure 1).

Figure 1 shows that $D_t(\Delta E)$ has large values only for $-2\pi\hbar/t<\Delta E<2\pi\hbar/t$ (the region between dashed lines), where the maximum $D_t(0)=t^2/\hbar^2$ increases rapidly with time. Furthermore, since $\int_{-\infty}^\infty D_t(x)\mathrm{d}x=2\pi t/\hbar$, we define the function

$$\delta_t(\Delta E)=\frac{\hbar}{2\pi t}D_t(\Delta E),$$

which is a representation of the $\delta$-function in the limit $t\rightarrow\infty$.

If we plug eq. 22 into eq. 21, 

$$P(t)=|a_s(t)|^2=|H_{sn}'|^2D_t(\Delta E)=\frac{2\pi t}{\hbar}\delta_t(E_s-E_n),$$

And the transition rate $R=\mathrm{d}P/\mathrm{d}t$ becomes

$$R=\frac{\mathrm{d}P}{\mathrm{d}t}=\frac{2\pi}{\hbar}|H_{sn}'|^2\delta_t(E_s-E_n),$$

Eq. 23 is another common representation of the Fermi-Golden Rule.

***

**Harmonic Perturbation**

So far, we've only considered the constant perturbation ($H'$ is independent of time once it is turned on). Now we consider the interaction of a system with an oscillating perturbation turned on at time $t_0=0$ (Figure 2). The results will be used to describe how a light field induces transitions in a system through dipole interactions.

Again, we are looking to calculate the transition probability between states $n$ and $s$. Here, we treat the light field classically:

$$H'=V(t)=V\cos(\omega t),$$

$$H'_{sn}(t)=V_{sn}\cos(\omega t)=\frac{V_{sn}}{2}[e^{-i\omega t}+e^{i\omega t}],$$

Setting $t_0\rightarrow 0$, first-order perturbation theory eq. 12 leads to 

$$a_s(t)=\frac{-i}{\hbar}\int_{t_0}^t V_{sn}(\tau)e^{i\omega_{sn}\tau}\mathrm{d}\tau=\frac{-iV_{sn}}{2\hbar}\int_0^t[e^{i(\omega_{sn}-\omega)\tau}+e^{i(\omega_{sn}+\omega)\tau}]\mathrm{d}\tau=\frac{-V_{sn}}{2\hbar}[\frac{e^{i(\omega_{sn}-\omega)t}-1}{\omega_{sn}-\omega}+\frac{e^{i(\omega_{sn}+\omega)t}-1}{\omega_{sn}+\omega}],$$

Since $e^{i\theta}-1=2ie^{i\theta/2}\sin(\theta/2)$

Eq. 27 becomes

$$a_s(t)=\frac{-iV_{sn}}{\hbar}[\frac{e^{i(\omega_{sn}-\omega)t/2}\sin[(\omega_{sn}-\omega)t/2]}{\omega_{sn}-\omega}+\frac{e^{i(\omega_{sn}+\omega)t/2}\sin[(\omega_{sn}+\omega)t/2]}{\omega_{sn}+\omega}],$$

The first term in eq. 28 is *absorption* while the second term is *stimulated emission*.

Notice that the terms in eq. 28 are only significant when $\omega\approx\pm\omega_{sn}$, that is, a matching of the frequency of the harmonic interaction with the energy splitting between quantum states. Consider the resonance conditions that will maximize each term (Figure 3):


**References**
1. Khurgin, J. B. How to deal with the loss in plasmonics and metamaterials. *Nat Nanotechnol* **2015**, *10* (1), 2-6.
2. Manjavacas, A.; Liu, J. G.; Kulkarni, V.; Nordlander, P. Plasmon-Induced Hot Carriers in Metallic Nanoparticles. *ACS Nano* **2014**, *8* (8), 7630-7638.
3. Govorov, A. O.; Zhang, H.; Gun’ko, Y. K. Theory of Photoinjection of Hot Plasmonic Carriers from Metal Nanostructures into Semiconductors and Surface Molecules. *The Journal of Physical Chemistry C* **2013**, *117* (32), 16616-16631.
4. Sundararaman, R.; Narang, P.; Jermyn, A. S.; Goddard Iii, W. A.; Atwater, H. A. Theoretical predictions for hot-carrier generation from surface plasmon decay. *Nature Communications* **2014**, *5* (1), 5788.
5. Brown, A. M.; Sundararaman, R.; Narang, P.; Goddard, W. A., 3rd; Atwater, H. A. Nonradiative Plasmon Decay and Hot Carrier Dynamics: Effects of Phonons, Surfaces, and Geometry. *ACS Nano* **2016**, *10* (1), 957-966.
6. Wu, S.; Sheldon, M. T. Optical Power Conversion via Tunneling of Plasmonic Hot Carriers. *ACS Photonics* **2018**, *5* (6), 2516-2523.
7. Wu, S.; Chen, Y.; Gao, S. Plasmonic Photocatalysis with Nonthermalized Hot Carriers. *Physical Review Letters* **2022**, *129* (8), 086801.


