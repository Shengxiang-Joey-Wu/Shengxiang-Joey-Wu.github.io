---
title: 'Calculating Plasmon-Induced Hot Carriers from Scratch'
date: 2023-01-06
permalink: /posts/2023/01/calculating-plasmon-induced-hot-carriers-from-scratch/
redirect_from:
  - /posts/2023/01/plasmon-induced-nonthermal-carriers/
excerpt: <img src="/images/blogImages/tutorial_3_thumbnail.jpg" width="598">
tags:
  - Plasmonics
  - Nonthermal Carriers
---
*Updated October 10, 2026.*

In the previous [tutorial](/posts/2022/09/plasmonic-nanostructures-from-resonance-to-hot-carriers/), I mentioned that the nonradiative damping of surface plasmons was historically viewed as a loss in the field of nanophotonics;<sup>1</sup> however, it is now a popular topic in the community of photocatalysis and photochemistry: chemists have realized that the "losses", if managed properly, can be turned into advantages to drive (uphill) chemical reactions and can even demonstrate certain bond selectivity that is not accessible by thermal means. 

The advantages are associated with energetic nonthermal or hot carriers that are generated after nonradiative damping of surface plasmons; it would therefore be useful if one could predict the energy distribution of nonthermal carriers for a given plasmonic nanoparticle. Indeed, there are multiple ways to perform such calculations, ranging from free-electron models<sup>2, 3</sup> to more rigorous treatments based on density functional theory (DFT).<sup>4, 5</sup> 

During my Ph.D. study and postdoctoral work, I followed [ref. 2](https://pubs.acs.org/doi/10.1021/nn502445f) to calculate the energy profile of nonthermal carriers and then applied it to model the tunneling current<sup>6</sup> and photocatalytic performance.<sup>7</sup> It turns out that the approach used here could also serve as an extracurricular activity for first-year graduate students or senior undergraduates to strengthen their understanding of quantum chemistry. In fact, the main result of ref. 2 can be reproduced by simply combining quantum chemistry and entry-level electromagnetics. Let's get started!

Preliminary Knowledge
======

**Fermi's Golden Rule**

"In quantum physics, Fermi's golden rule is a formula that describes the transition rate (the probability of a transition per unit time) from one energy eigenstate of a quantum system to a group of energy eigenstates in a continuum, as a result of a weak perturbation" — Wikipedia.

[Fermi's golden rule](https://en.wikipedia.org/wiki/Fermi%27s_golden_rule) is the tool that we will use to analyze our problem, since we are interested in the transition probability of exciting an electron (hole), after nonradiative decay of excited plasmons, from its initial state to all possible final states. Therefore, before I throw you into a math puzzle, let me walk you through the fundamentals of Fermi's golden rule. (You can also find the derivation of Fermi's golden rule in many textbooks and online materials.)

The modeling of plasmonic nonthermal carriers is essentially a perturbation problem. For now, let's assume the perturbation is a constant value $H'$ (we will consider the effect of localized surface plasmon later); the Hamiltonian of the system can be written as

$$H=H_0+H',$$

where $H_0$ is the unperturbed Hamiltonian and $H'$ represents the perturbation. Let's say the unperturbed wavefunction $\Psi_0$ satisfies the time-dependent Schrödinger equation (TDSE):

$$i\hbar\frac{\partial\Psi_0}{\partial t}=H_0\Psi_0,$$

where the wavefunction $\Psi_0$ has the generic form:

$$\Psi_0=\psi_0(\mathbf{r})e^{-iE_0t/\hbar}.$$

Since the Hamiltonian (Energy) operator is a Hermitian operator, its eigenfunctions shall form a complete set. Let's use $\vert u\rangle$ to represent the eigenfunctions of $H_0$, that is, $\vert u\rangle=\lbrace u_1^0,u_2^0,\dots,u_n^0\rbrace$. Because any wavefunction can be represented as a linear combination of the eigenfunctions (if these eigenfunctions form a complete set), eq. 3 can be written more generally as

$$\Psi_0=\sum_na_n^0u_n^0e^{-iE_n^0t/\hbar}.$$

The subscript and superscript $0$ denote the unperturbed system.
The unperturbed state described by $H_0$ has a set of energy eigenvalues such that

$$H_0u_n^0=E_n^0u_n^0.$$

By comparing eq. 3 and eq. 4 at $t=0$, it is easy (hopefully for you as well) to tell that $\psi_0(\mathbf{r})=\sum_na_n^0u_n^0$ (a wavefunction can be described as a linear combination of a complete orthonormal set $\vert u\rangle$). Note that the expansion coefficients $a_n^0$ are independent of time.

Suppose now we have a state described by wavefunction $\Psi$, and we are interested in how this wavefunction evolves (after the perturbation $H'$). We then put the wavefunction $\Psi$ in eq. 1 and use the TDSE

$$H\Psi=i\hbar\frac{\partial\Psi}{\partial t}=(H_0+H')\Psi,$$

and

$$\Psi=\sum_na_n(t)u_n^0e^{-iE_n^0t/\hbar}.$$

Note that now the prefactors $a_n(t)$ depend on time.
Substituting eq. 7 into eq. 6, multiplying by the complex conjugate $u_s^{0*}$ and using the orthonormality of the wavefunctions, we obtain


$$\frac{\mathrm{d}a_s}{\mathrm{d}t}=\frac{-i}{\hbar}\sum_na_n(t)H_{sn}'e^{i(E_s^0-E_n^0)t/\hbar},$$

where

$$H_{sn}'=\int u_s^{0*}H'u_n^0\mathrm{d}\tau.$$


The $\int\mathrm{d}\tau$ denotes integration over the full range of all the coordinates of a system.

For a small perturbation, the time variation of $a_n(t)$ is slow, so $a_n(t)\cong a_n(0)$ and

$$a_s(t)-a_s(0)\cong\frac{-i}{\hbar}\sum_na_n(0)\int_0^tH_{sn}'(t')e^{i\omega_{sn}t'}\mathrm{d}t',$$

where 

$$\hbar\omega_{sn}=E_s^0-E_n^0.$$

For simplicity, consider the special case in which the system is in state $n$ at $t=0$, that is, $a_n(0)=1$ and all other $a_{s\neq n}(0)=0$. Then

$$a_s(t)=\frac{-i}{\hbar}\int_0^tH'_{sn}(t')e^{i\omega_{sn}t'}\mathrm{d}t'\qquad\mathrm{for}\;s\neq n.$$

Eq. 12 shows that $H'(t)$ can induce transitions from state $n$ to other states ($s\neq n$).

If $H'$ is independent of time,

$$a_s(t)=\frac{-i}{\hbar}H'_{sn}\int_0^te^{i\omega_{sn}t'}\mathrm{d}t'=-H_{sn}'\frac{(e^{i\omega_{sn}t}-1)}{\hbar\omega_{sn}}.$$

Therefore,

$$\vert a_s(t)\vert^2=4\vert H'_{sn}\vert^2\sin^2(\frac{\omega_{sn}t}{2})/(\hbar^2\omega_{sn}^2).$$

Now we can perform some mathematical tricks on eq. 14, 

$$\vert a_s(t)\vert^2=4\vert H'_{sn}\vert^2\sin^2(\frac{\omega_{sn}t}{2})/(\hbar^2\omega_{sn}^2) \\
=\frac{\vert H_{sn}'\vert^2}{\hbar^2}t^2\frac{\sin^2(\omega_{sn}t/2)}{\omega_{sn}^2t^2/4}=\frac{\vert H_{sn}'\vert^2}{\hbar^2}t^2\mathrm{sinc}^2(\omega_{sn}t/2).$$

Since $\lim\limits_{x\rightarrow 0}\mathrm{sinc}(x)=1$, for short times eq. 15 becomes

$$|a_s(t)|^2=\frac{|H_{sn}'|^2}{\hbar^2}t^2.$$

Thus, the short-time behavior is *quadratic* in time.

In the long-time limit ($t\rightarrow\infty$), we also rewrite eq. 14 as 

$$\vert a_s(t)\vert^2=4\vert H'_{sn}\vert^2\sin^2(\frac{\omega_{sn}t}{2})/(\hbar^2\omega_{sn}^2)=4\vert H_{sn}'\vert^2\sin^2(\frac{\Delta Et}{2\hbar})/(\Delta E)^2.$$

Here, we've defined $\Delta E=E_s-E_n=\omega_{sn}\hbar$. Let us further define a function $D_t(\Delta E)\equiv4\sin^2(\frac{\Delta Et}{2\hbar})/(\Delta E)^2$ and plot $D_t(\Delta E)$ vs. $\Delta E$ to visualize its properties (Figure 1).

<p align="center">
<img src="/images/blogImages/tutorial_3_figure_01.jpg" width="331">
</p>  

Figure 1 shows that $D_t(\Delta E)$ has large values only for $-2\pi\hbar/t<\Delta E<2\pi\hbar/t$, where the maximum $D_t(0)=t^2/\hbar^2$ increases rapidly with time. Furthermore, since $\int_{-\infty}^\infty D_t(x)\mathrm{d}x=2\pi t/\hbar$, we define another function

$$\delta_t(\Delta E)=\frac{\hbar}{2\pi t}D_t(\Delta E),$$

which is a representation of the $\delta$-function in the limit $t\rightarrow\infty$.

If we plug eq. 18 into eq. 17, 

$$P(t)=|a_s(t)|^2=|H_{sn}'|^2D_t(\Delta E)=\frac{2\pi t}{\hbar}|H_{sn}'|^2\delta_t(E_s-E_n).$$

And the transition rate $R=\mathrm{d}P/\mathrm{d}t$ becomes

$$R=\frac{\mathrm{d}P}{\mathrm{d}t}=\frac{2\pi}{\hbar}|H_{sn}'|^2\delta_t(E_s-E_n).$$

Eq. 20 is indeed the well-known Fermi's golden rule.

***

**Harmonic Perturbation**

So far, we've only considered the constant perturbation, that is, $H'$ is independent of time once it is turned on. Now we consider the interaction with an oscillating perturbation turned on at time $t_0=0$ (Figure 2). The results will be used to describe how a light field induces transitions in a system through dipole interactions.

<p align="center">
<img src="/images/blogImages/tutorial_3_figure_02.jpg" width="458">
</p>  

Again, we want to know the rate of transition between states $n$ and $s$. Here, we treat the light field classically:

$$H'=V(t)=V\cos(\omega t),$$

$$H'_{sn}(t)=V_{sn}\cos(\omega t)=\frac{V_{sn}}{2}[e^{-i\omega t}+e^{i\omega t}].$$

Setting $t_0\rightarrow 0$ and substituting eq. 22 into eq. 12,

$$a_s(t)=\frac{-i}{\hbar}\int_{t_0}^t V_{sn}(t')e^{i\omega_{sn}t'}\mathrm{d}t'=\frac{-iV_{sn}}{2\hbar}\int_0^t[e^{i(\omega_{sn}-\omega)t'}+e^{i(\omega_{sn}+\omega)t'}]\mathrm{d}t' \\
=\frac{-V_{sn}}{2\hbar}[\frac{e^{i(\omega_{sn}-\omega)t}-1}{\omega_{sn}-\omega}+\frac{e^{i(\omega_{sn}+\omega)t}-1}{\omega_{sn}+\omega}].$$

Since $e^{i\theta}-1=2ie^{i\theta/2}\sin(\theta/2)$, eq. 23 becomes

$$a_s(t)=\frac{-iV_{sn}}{\hbar}[\frac{e^{i(\omega_{sn}-\omega)t/2}\sin[(\omega_{sn}-\omega)t/2]}{\omega_{sn}-\omega}+\frac{e^{i(\omega_{sn}+\omega)t/2}\sin[(\omega_{sn}+\omega)t/2]}{\omega_{sn}+\omega}].$$

The first term in eq. 24 is *absorption*, and the second is *stimulated emission*.

Notice that the terms in eq. 24 are only significant when $\omega\approx\pm\omega_{sn}$, that is, a matching of the frequency of the harmonic interaction with the transition energy between quantum states (Figure 3).

<p align="center">
<img src="/images/blogImages/tutorial_3_figure_03.jpg" width="412">
</p>  

We first analyze the absorption part:

$$P(t)=\vert a_s(t)\vert^2=\frac{\vert V_{sn}\vert^2}{\hbar^2(\omega_{sn}-\omega)^2}\sin^2[\frac{1}{2}(\omega_{sn}-\omega)t].$$

We then do a similar transformation as in eqs. 17–18,

$$P(t)=|V_{sn}|^2\frac{\sin^2[\frac{1}{2}(\omega_{sn}-\omega)\hbar t/\hbar]}{\hbar^2(\omega_{sn}-\omega)^2} \\
=|V_{sn}|^2\frac{\sin^2[\frac{1}{2}\Delta Et/\hbar]}{\Delta E^2} \\
=\frac{\pi t}{2\hbar}|V_{sn}|^2\delta_t(\Delta E) \\
=\frac{\pi t}{2\hbar}|V_{sn}|^2\delta_t(\hbar(\omega_s-\omega_n-\omega)).$$

Note that $\Delta E$ here is defined as $\Delta E\equiv\hbar(\omega_s-\omega_n-\omega)$. The transition rate for this absorption process is therefore

$$R_{\mathrm{abs}}=\frac{\mathrm{d}P(t)}{\mathrm{d}t}=\frac{\pi}{2\hbar}|V_{sn}|^2\delta_t(\hbar(\omega_s-\omega_n-\omega)).$$

Similarly, the transition rate for the stimulated emission process is

$$R_{\mathrm{em}}=\frac{\pi}{2\hbar}|V_{sn}|^2\delta_t(\hbar(\omega_s-\omega_n+\omega)).$$

The overall transition rate (probability per unit time) from state $n$ to state $s$ is then

$$R=R_{\mathrm{abs}}+R_{\mathrm{em}}=\frac{\pi}{2\hbar}|V_{sn}|^2\delta_t(\hbar(\omega_s-\omega_n-\omega))+\frac{\pi}{2\hbar}|V_{sn}|^2\delta_t(\hbar(\omega_s-\omega_n+\omega)).$$

Note that in the long-time limit, we neglect interference between the resonant and anti-resonant terms.

Furthermore, the Dirac delta function can be expressed as a Lorentzian to account for the relaxation process,

$$\delta(\hbar(\omega_s-\omega_n\pm\omega))=\delta(\varepsilon_f-\varepsilon_i\pm\hbar\omega)=\frac{1}{\pi}\lim_{\gamma\rightarrow 0}\frac{\gamma}{(\varepsilon_f-\varepsilon_i\pm\hbar\omega)^2+\gamma^2}.$$

Note here that we define $\hbar\omega_s\equiv\varepsilon_f$ and $\hbar\omega_n\equiv\varepsilon_i$; the subscripts $f$ and $i$ denote the final and initial states.

By introducing a damping factor $\gamma=\hbar/\tau$ in eq. 30, and substituting eq. 30 in eq. 29 (note that we switched notation here: $M_{fi}=V_{sn}/2$ is the matrix element of the $e^{-i\omega t}$ component of the perturbation in eq. 22, so $\vert M_{fi}\vert^2=\vert V_{sn}\vert^2/4$), we obtain

$$R=\frac{2}{\tau}[\frac{\vert M_{fi}\vert^2}{(\varepsilon_f-\varepsilon_i-\hbar\omega)^2+(\hbar/\tau)^2}+\frac{\vert M_{fi}\vert^2}{(\varepsilon_f-\varepsilon_i+\hbar\omega)^2+(\hbar/\tau)^2}].$$

After accounting for the spin and the occupation probability dictated by the Fermi–Dirac distribution, eq. 31 becomes

$$R=\frac{4}{\tau}f(\varepsilon_i)(1-f(\varepsilon_f))[\frac{\vert M_{fi}\vert^2}{(\varepsilon_f-\varepsilon_i-\hbar\omega)^2+(\hbar/\tau)^2}+\frac{\vert M_{fi}\vert^2}{(\varepsilon_f-\varepsilon_i+\hbar\omega)^2+(\hbar/\tau)^2}].$$

If one considers all the possible initial states, eq. 32 becomes eq. 1 of ref. 2.

Wavefunctions of Spherical Nanoparticles
=====

Then we need to find the appropriate basis set for conduction electrons in plasmonic nanoparticles. For simplicity, we consider nanoparticles with a spherical shape, which leaves us with a central-force problem when solving the Schrödinger equation:

$$\hat{H}=\hat{T}+\hat{V}=-(\frac{\hbar^2}{2m})\nabla^2+V(r),$$

where $\nabla^2\equiv\frac{\partial^2}{\partial x^2}+\frac{\partial^2}{\partial y^2}+\frac{\partial^2}{\partial z^2}$.

For a sphere, it is convenient to work in spherical coordinates, so we rewrite the Laplace operator in spherical coordinates,

$$\nabla^2\equiv\frac{\partial^2}{\partial r^2}+\frac{2}{r}\frac{\partial}{\partial r}+\frac{1}{r^2}\frac{\partial^2}{\partial\theta^2}+\frac{1}{r^2}\cot{\theta}\frac{\partial}{\partial\theta}+\frac{1}{r^2\sin^2\theta}\frac{\partial^2}{\partial\phi^2}.$$

It can be shown that (in any quantum mechanics/chemistry book) 

$$\hat{L}^2=-\hbar^2(\frac{\partial^2}{\partial\theta^2}+\cot\theta\frac{\partial}{\partial\theta}+\frac{1}{\sin^2{\theta}}\frac{\partial^2}{\partial\phi^2}),$$

where $\hat{L}$ is the angular momentum operator.

Therefore, eq. 33 is transformed to

$$\hat{H}=-\frac{\hbar^2}{2m}(\frac{\partial^2}{\partial r^2}+\frac{2}{r}\frac{\partial}{\partial r})+\frac{1}{2mr^2}\hat{L}^2+V(r).$$

And it can also be shown that 

$$[\hat{H}, \hat{L}^2]=0\qquad \mathrm{if}\;V=V(r) \\

[\hat{H}, \hat{L}_z]=0\qquad\mathrm{if}\;V=V(r).$$

Thus, it is possible to have a set of simultaneous eigenfunctions of $\hat{H}$, $\hat{L}^2$, and $\hat{L}_z$ for the central-force problem,

$$\hat{H}\psi=E\psi;\qquad\hat{L}^2\psi=l(l+1)\hbar^2\psi,\;\;\;l=0,1,2,...\\
\hat{L}_z\psi=m\hbar\psi,\;\;\;m=-l,-l+1,...,l.$$

Using the above eigenvalues, eq. 36 can be transformed as

$$-\frac{\hbar^2}{2m}(\frac{\partial^2\psi}{\partial r^2}+\frac{2}{r}\frac{\partial\psi}{\partial r})+\frac{l(l+1)\hbar^2}{2mr^2}\psi+V(r)\psi=E\psi.$$

The eigenfunctions of $\hat{L}^2$ are spherical harmonics $Y_l^m(\theta, \phi)$, and since $\hat{L}^2$ does not involve $r$, it is possible to multiply $Y_l^m$ by an arbitrary function of $r$ and still have eigenfunctions of $\hat{L}^2$ and $\hat{L}_z$.

$$\psi=R(r)Y_l^m(\theta,\phi).$$

Plugging the variable-separated wavefunction into eq. 39 and dividing both sides by $Y_l^m$, one gets an ordinary differential equation for the unknown function $R(r)$

$$-\frac{\hbar^2}{2m}(R''+\frac{2}{r}R')+[\frac{l(l+1)\hbar^2}{2mr^2}+V(r)]R=ER.$$

Then we transform eq. 41 a little bit and then look up the mathematical solution (sometimes a friend majoring in mathematics is a plus),

$$-\frac{\hbar^2}{2m}(R''+\frac{2}{r}R')+[\frac{l(l+1)\hbar^2}{2mr^2}+V(r)]R=ER \\
\Rightarrow -\frac{\hbar^2}{2m}(R''+\frac{2}{r}R')+[(V(r)-E)+\frac{l(l+1)\hbar^2}{2mr^2}]R=0 \\
\Rightarrow R''+\frac{2}{r}R'-[\frac{2m}{\hbar^2}(V(r)-E)+\frac{l(l+1)}{r^2}]R=0 \\
\Rightarrow r^2R''+2rR'-[\frac{2mr^2}{\hbar^2}(V(r)-E)+l(l+1)]R=0 \\
\Rightarrow r^2R''+2rR'+[-\frac{2mr^2}{\hbar^2}(V(r)-E)-l(l+1)]R=0.$$

Try $R$ as $y(x)$ and $x=kr$, $k=\sqrt{\frac{-2m(V(r)-E)}{\hbar^2}}$. This substitution is only valid where $V(r)$ is constant, so that $k$ does not depend on $r$; for the spherical potential well considered below, that is the case inside and outside the sphere separately.

$$\frac{dR}{dr}=\frac{dR}{dx}\frac{dx}{dr}=\frac{dy}{dx}\sqrt{\frac{-2m(V(r)-E)}{\hbar^2}}\qquad\frac{d^2R}{dr^2}=\frac{d\frac{dR}{dr}}{dx}\frac{dx}{dr}=\frac{d^2y}{dx^2}\frac{-2m(V(r)-E)}{\hbar^2}.$$

Thus, eq. 42 becomes

$$\frac{-2m(V(r)-E)}{\hbar^2}r^2\frac{d^2y}{dx^2}+2r\sqrt{\frac{-2m(V(r)-E)}{\hbar^2}}\frac{dy}{dx}+[-\frac{2mr^2}{\hbar^2}(V(r)-E)-l(l+1)]y=0.$$

Since $x=\sqrt{\frac{-2m(V(r)-E)}{\hbar^2}}r$, the above equation becomes

$$x^2\frac{d^2y}{dx^2}+2x\frac{dy}{dx}+(x^2-l(l+1))y=0.$$

It turns out that eq. 45 has analytical solutions: the two linearly independent solutions are spherical Bessel functions of the first kind $j_l$ and spherical Bessel functions of the second kind $y_l$.

$$j_l(x)=(-x)^l(\frac{1}{x}\frac{d}{dx})^l\frac{\sin{x}}{x},\qquad y_l(x)=-(-x)^l(\frac{1}{x}\frac{d}{dx})^l\frac{\cos{x}}{x}.$$

***
**Finite Spherical Potential Well**

Instead of an infinite potential well, as quantum chemistry textbooks usually consider, here we consider a more realistic scenario (Figure 4), that is, the potential inside the spherical nanoparticles, of radius $r_0$ (labeled $R$ in Figure 4), has a finite value $V_0$, and the potential outside the nanoparticle is $0$ (vacuum level).

<p align="center">
<img src="/images/blogImages/tutorial_3_figure_04.jpg" width="400">
</p>  

Note that $V_0$ is negative here, and the bound states we are looking for have energies $V_0<E<0$. From eq. 46, one may write down the wavefunction inside the nanosphere, which is $\psi_\mathrm{in}=j_l(kr)$ with $k=\sqrt{\frac{2m(E-V_0)}{\hbar^2}}$. Outside the sphere the potential is $0$ and $E<0$, so the wavefunction must decay with distance: $\psi_\mathrm{out}=k_l(\kappa r)$ with $\kappa=\sqrt{\frac{-2mE}{\hbar^2}}$, where $k_l(x)$ is the modified spherical Bessel function of the second kind. It is purely real, and it is equivalent (up to a constant factor) to the spherical Hankel function of the first kind, $h_l(x)=j_l(x)+iy_l(x)$, evaluated at the imaginary argument $i\kappa r$.

Then we need to apply boundary conditions to find eigenenergies: the wavefunction needs to be continuous and smooth. Continuity requires that the wavefunctions match at the surface of the nanosphere, while smoothness requires that their first derivatives also match at the surface.

$$\mathrm{Continuous:\qquad\psi_\mathrm{in}=\psi_\mathrm{out}}\bigg\rvert_{r=r_0};\qquad \mathrm{Smooth: \frac{d\psi_\mathrm{in}}{dr}}=\frac{d\psi_\mathrm{out}}{dr}\bigg\rvert_{r=r_0}.$$

Rather than solving the two conditions separately, the logarithmic derivative is used instead

$$\frac{\frac{d\psi_\mathrm{in}}{dr}}{\psi_\mathrm{in}}=\frac{\frac{d\psi_\mathrm{out}}{dr}}{\psi_\mathrm{out}}\bigg\rvert_{r=r_0},$$

which reads

$$k\frac{j_l'(kr)}{j_l(kr)}\bigg\rvert_{r=r_0}-\kappa\frac{k_l'(\kappa r)}{k_l(\kappa r)}\bigg\rvert_{r=r_0}=0.$$

Then the allowed energy (implicitly included in $k$ and $\kappa$) can be found by searching for the roots of eq. 49. We can repeat this procedure for all possible $l$, and Figure 5a summarizes these results for a $D=25\;\mathrm{nm}$ silver sphere. Furthermore, we can also visualize the broadened density of states (DOS), as shown in Figure 5b; it matches well with the three-dimensional free-electron-gas models in solid-state physics as expected.

<p align="center">
<img src="/images/blogImages/tutorial_3_figure_05.jpg" width="683">
</p>  

The parameter $V_0$ is crucial since it determines the material's work function. For the $D=25\;\mathrm{nm}$ Ag nanosphere in Figures 5 and 6, we choose $V_0=-10.04\;\mathrm{eV}$ to ensure the correct work function ($\sim4.5\;\mathrm{eV}$).  For a wavefunction to be well-behaved, we require it to be normalized, $\int_{-\infty}^\infty \psi^*\psi\mathrm{d}\tau=1$. After normalization, we can pick three random state wavefunctions of the same $D=25\;\mathrm{nm}$ sphere (Figure 6) to visualize that the boundary conditions are fulfilled. As shown in Figure 6, the wavefunctions we found are indeed continuous and smooth across the interface (solid line for inside the sphere, and dashed line for outside the sphere).

<p align="center">
<img src="/images/blogImages/tutorial_3_figure_06.jpg" width="420">
</p>  

Nonthermal Carrier Generation
=====

Now we have all the tools we need to calculate the generation rate and energy distribution of nonthermal carriers: we are equipped with the formula derived from Fermi's golden rule and the wavefunctions to describe the conduction band electrons in nanospheres. By looking at eq. 32, we realize the only remaining puzzle is the transition matrix element $M_{fi}=\langle\psi_f\vert eV'\vert\psi_i\rangle$, where $V'$ is the **overall** potential that electrons feel when the illumination is on. The overall potential for nanospheres can be written as $V'=V_{ext}+V_p$, where $V_{ext}$ is the external potential and $V_p$ is the plasmon-induced potential; the latter can be written as (from entry-level electromagnetics books):

$$V_p(r,\omega)=\begin{cases} \frac{\varepsilon-1}{\varepsilon+2}E_0r\cos\theta\qquad\mathrm{inside\;sphere}\\\frac{\varepsilon-1}{\varepsilon+2}\frac{r_0^3}{r^2}E_0\cos\theta\qquad\mathrm{outside\;sphere}\end{cases}.$$

And the external perturbation is simply $V_{ext}=-E_0r\cos\theta$. For silver, we use the Drude model $\varepsilon=\varepsilon_\mathrm{b}-\frac{\omega_{pl}^2}{\omega^2+i\omega\gamma_p}$ with background dielectric function $\varepsilon_\mathrm{b}=4.18$, a plasma frequency $\omega_{pl}=9.07\;\mathrm{eV}$, and a plasmon damping of $\gamma_p=60\;\mathrm{meV}$.<sup>2</sup> 

One more trick to note: the transition matrix element is evaluated as

$$\vert M_{fi}\vert^2=\vert \langle\psi_f\vert eV'\vert\psi_i\rangle\vert^2=e^2E_0^2\vert\langle R_f\vert v(r)\vert R_i\rangle\vert ^2\vert \langle Y_{l_f}^{m_f}\vert\cos\theta\vert Y_{l_i}^{m_i}\rangle\vert^2,$$

where $v(r)$ is the radial part of the overall potential, defined through $V'=E_0v(r)\cos\theta$. Luckily, we do not need to deal with the explicit expression: it turns out that $\vert\langle Y_{l_f}^{m_f}\vert\cos\theta\vert Y_{l_i}^{m_i}\rangle\vert^2$ can be evaluated analytically as

$$\vert\langle Y_{l_f}^{m_f}|\cos\theta|Y_{l_i}^{m_i}\rangle|^2=\frac{(l_\mathrm{min}-m+1)(l_\mathrm{min}+m+1)}{(2l_\mathrm{min}+3)(2l_\mathrm{min}+1)},$$

where $l_\mathrm{min}$ is the smaller of $l_f$ and $l_i$. Note the selection rule is that $l_f-l_i=\pm 1$ and $m_f=m_i$.

**Finally**, we can put everything together and evaluate the transition probability per unit time (equivalently, the excitation rate) using eq. 32, this time for a $D=15\;\mathrm{nm}$ silver nanosphere (Figure 7). For comparison, we also show the results from ref. 2 alongside. 

<p align="center">
<img src="/images/blogImages/tutorial_3_figure_07.jpg" width="611">
</p>  

Note: the axes of Figure 7 are labeled "hot carriers", following the terminology of ref. 2. The carriers calculated here are the *nonthermal* carriers in the sense of the [previous tutorial](/posts/2022/09/plasmonic-nanostructures-from-resonance-to-hot-carriers/): they are generated directly by plasmon decay and have not yet relaxed into a Fermi–Dirac-like distribution. Much of the literature uses the two terms interchangeably.

If you are interested in the detailed MATLAB code to perform this calculation, please email me at joeysxwu@gmail.com.



**References**
1. Khurgin, J. B. How to deal with the loss in plasmonics and metamaterials. *Nat. Nanotechnol.* **10**, 2–6 (2015).
2. Manjavacas, A., Liu, J. G., Kulkarni, V. & Nordlander, P. Plasmon-induced hot carriers in metallic nanoparticles. *ACS Nano* **8**, 7630–7638 (2014).
3. Govorov, A. O., Zhang, H. & Gun’ko, Y. K. Theory of photoinjection of hot plasmonic carriers from metal nanostructures into semiconductors and surface molecules. *J. Phys. Chem. C* **117**, 16616–16631 (2013).
4. Sundararaman, R., Narang, P., Jermyn, A. S., Goddard, W. A. III & Atwater, H. A. Theoretical predictions for hot-carrier generation from surface plasmon decay. *Nat. Commun.* **5**, 5788 (2014).
5. Brown, A. M., Sundararaman, R., Narang, P., Goddard, W. A. III & Atwater, H. A. Nonradiative plasmon decay and hot carrier dynamics: effects of phonons, surfaces, and geometry. *ACS Nano* **10**, 957–966 (2016).
6. Wu, S. & Sheldon, M. T. Optical power conversion via tunneling of plasmonic hot carriers. *ACS Photonics* **5**, 2516–2523 (2018).
7. Wu, S., Chen, Y. & Gao, S. Plasmonic photocatalysis with nonthermalized hot carriers. *Phys. Rev. Lett.* **129**, 086801 (2022).


