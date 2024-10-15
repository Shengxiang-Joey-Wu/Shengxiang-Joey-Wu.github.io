---
title: 'Plasmon Induced Nonthermal Carriers'
date: 2023-01-06
permalink: /posts/2023/01/plasmon-induced-nonthermal-carriers/
excerpt: <img src="http://Shengxiang-Joey-Wu.github.io/images/blogImages/pinc_TOC.jpg" width="598">
tags:
  - Plasmonics
  - Nonthermal Carriers
---

In the previous [blog](https://shengxiang-joey-wu.github.io/posts/2022/09/what-is-plasmonic-nanostructure/), I mentioned that the non-radiative damping of surface plasmon was historically viewed as losses in the field of nanophotonics,<sup>1</sup> however, it is now a popular topic in the community of photocatalysis and photochemistry - the chemists realized that the 'losses', if managed properly, can be turned into advantages to drive (uphill) chemical reactions and can even demonstrate certain bond selectivity that is not accessible by thermal means. 

The advantages are associated with energetic nonthermal or hot carriers that are generated after non-radiative damping of surface plasmons, therefore it would be nice if one can predict the energy distribution of nonthermal carriers for given plasmonic nanoparticles. Indeed, there are multiple ways to perform such calculations from free-electron-like algorithms<sup>2, 3</sup> to more rigorous treatments based on density functional theory (DFT).<sup>4, 5</sup> 

During my Ph.D. study and postdoctoral work, I have followed [ref. 2](https://pubs.acs.org/doi/10.1021/nn502445f) to calculate the energy profile of nonthermal carriers and then apply it to model the tunneling current<sup>6</sup> and photocatalytic performance.<sup>7</sup> It turns out that the approach used here could also serve as an extracurricular activity for first-year graduate students or senior undergraduates to strengthen their understanding of quantum chemistry. That being said, the replication of the major result of ref. 2 can be performed by simply combining quantum chemistry and entry-level electromagnetics. Let's get started!

Preliminary Knowledge
======

**Fermi's Golden Rule**

"In quantum physics, Fermi's golden rule is a formula that describes the transition rate (the probability of a transition per unit time) from one energy eigenstate of a quantum system to a group of energy eigenstates in a continuum, as a result of a weak perturbation" — Wikipedia.

[Fermi's Golden rule](https://en.wikipedia.org/wiki/Fermi%27s_golden_rule) is the tool that we will use to analyze our problem, since we are interested in the transition probability of exciting an electron (hole), after non-radiative decay of excited plasmons, from its initial state to all possible final states. Therefore, before I throw you into a math puzzle, let me walk you through the fundamentals of Fermi's Golden rule. (You can also find the derivation of the Fermi-Golden rule in many textbooks and online materials.)

The modeling of plasmonic nonthermal carriers is essentially a perturbation problem, let's, for now, assume the perturbation is a constant value $H'$ (we will consider the effect of localized surface plasmon later), then the Hamiltonian of the system can be written as

$$H=H_0+H',$$

where $H_0$ is the unperturbed Hamiltonian and $H'$ represents perturbation. Let's say $H_0$ satisfied the time-dependent $\mathrm{Schr\ddot{o}dinger}$ equation (TDSE):

$$i\hbar\frac{\partial\Psi_0}{\partial t}=H_0\Psi_0,$$

where the wavefunction $\Psi_0$ has the generic form:

$$\Psi_0=\psi_0(\mathbf{r})e^{-iE_0t/\hbar},$$

Since the Hamiltonian (Energy) operator is a Hermitian operator, its eigenfunctions shall form a complete set. Let's use $\vert u\rangle$ represents the eigenfunctions of $H_0$, that is, $\vert u\rangle=\{u_1,u_2,\dots,u_n\}$. Because any wavefunctions can be represented as the linear combination of the eigenfunctions (if these eigenfunctions form a complete set), eq. 3 can be written more generally as

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

For a small perturbation, the time variation of $a_n(t)$ is slow, so $a_n(t)\cong a_n(0)$ and

$$a_s(t)-a_s(0)\cong\frac{-i}{\hbar}\sum_na_n(0)\int_0^tH_{sn}'(t')e^{i\omega_{sn}t'}\mathrm{d}t',$$

where 

$$\hbar\omega_{sn}=E_s^0-E_n^0,$$

If, for simplicity, we consider the special case for which the system is in state $n$ at $t=0$, that is, $a_n(0)=1$ and all other $a_{s\neq n}(0)=0$. Then

$$a_s(t)=\frac{-i}{\hbar}\int_0^tH'_{sn}(t')e^{i\omega_{sn}t'}\mathrm{d}t'\qquad\mathrm{for}\;s\neq n,$$

The eq. 12 just showed that $H'(t)$ can induce transitions from state $n$ to other states ($s\neq n$).

If $H'$ is independent of time,

$$a_s(t)=\frac{-i}{\hbar}H'_{sn}\int_0^te^{i\omega_{sn}t'}\mathrm{d}t'=-H_{sn}'\frac{(e^{i\omega_{sn}t}-1)}{\hbar\omega_{sn}},$$

Therefore,

$$\vert a_s(t)\vert^2=4\vert H'_{sn}\vert^2\sin^2(\frac{\omega_{sn}t}{2})/(\hbar^2\omega_{sn}^2),$$

Now we can perform some mathematical tricks on eq. 14, 

$$\vert a_s(t)\vert^2=4\vert H'_{sn}\vert^2\sin^2(\frac{\omega_{sn}t}{2})/(\hbar^2\omega_{sn}^2) \\
=\frac{\vert H_{sn}'\vert^2}{\hbar^2}t^2\frac{\sin^2(\omega_{sn}t/2)}{\omega_{sn}^2t^2/4}=\frac{\vert H_{sn}'\vert^2}{\hbar^2}t^2\mathrm{sinc}^2(\omega_{sn}t/2),$$

Since $\lim\limits_{x\rightarrow 0}\mathrm{sinc}(x)=1$, eq. 15 becomes

$$|a_s(t)|^2=\frac{|H_{sn}'|^2}{\hbar^2}t^2,$$

Thus, the short-time behavior is *quadratic* with time.

For the long time limit ($t\rightarrow\infty$), we also rewrite eq. 14 as 

$$\vert a_s(t)\vert^2=4\vert H'_{sn}\vert^2\sin^2(\frac{\omega_{sn}t}{2})/(\hbar^2\omega_{sn}^2)=4\vert H_{sn}'\vert^2\sin^2(\frac{\Delta Et}{2\hbar})/(\Delta E)^2,$$

Here, we've defined $\Delta E=E_s-E_n=\omega_{sn}\hbar$. Let us further define a function $D_t(\Delta E)\equiv4\sin^2(\frac{\Delta Et}{2\hbar})/(\Delta E)^2$, we plot $D_t(\Delta E)$ vs. $\Delta E$ to visualize its properties (Figure 1).

<p align="center">
<img src="http://ShengxiangWuPlasmonic.github.io/images/blogImages/pinc_Figure1.jpg" width="331">
</p>  

Figure 1 shows that $D_t(\Delta E)$ has large values only for $-2\pi\hbar/t<\Delta E<2\pi\hbar/t$ (the region between dashed lines), where the maximum $D_t(0)=t^2/\hbar^2$ increases rapidly with time. Furthermore, since $\int_{-\infty}^\infty D_t(x)\mathrm{d}x=2\pi t/\hbar$, we define another function

$$\delta_t(\Delta E)=\frac{\hbar}{2\pi t}D_t(\Delta E),$$

which is a representation of the $\delta$-function in the limit $t\rightarrow\infty$.

If we plug eq. 18 into eq. 17, 

$$P(t)=|a_s(t)|^2=|H_{sn}'|^2D_t(\Delta E)=\frac{2\pi t}{\hbar}\delta_t(E_s-E_n),$$

And the transition rate $R=\mathrm{d}P/\mathrm{d}t$ becomes

$$R=\frac{\mathrm{d}P}{\mathrm{d}t}=\frac{2\pi}{\hbar}|H_{sn}'|^2\delta_t(E_s-E_n),$$

Eq. 20 is indeed the well-known Fermi's Golden Rule.

***

**Harmonic Perturbation**

So far, we've only considered the constant perturbation, that is, $H'$ is independent of time once it is turned on. Now we consider the interaction with an oscillating perturbation turned on at time $t_0=0$ (Figure 2). The results will be used to describe how a light field induces transitions in a system through dipole interactions.

<p align="center">
<img src="http://Shengxiang-Joey-Wu.github.io/images/blogImages/pinc_Figure2.jpg" width="458">
</p>  

Again, we want to know the rate of transition between states $n$ and $s$. Here, we treat the light field classically:

$$H'=V(t)=V\cos(\omega t),$$

$$H'_{sn}(t)=V_{sn}\cos(\omega t)=\frac{V_{sn}}{2}[e^{-i\omega t}+e^{i\omega t}],$$

Setting $t_0\rightarrow 0$, and substitute eq. 22 into eq. 12,

$$a_s(t)=\frac{-i}{\hbar}\int_{t_0}^t V_{sn}(\tau)e^{i\omega_{sn}\tau}\mathrm{d}\tau=\frac{-iV_{sn}}{2\hbar}\int_0^t[e^{i(\omega_{sn}-\omega)\tau}+e^{i(\omega_{sn}+\omega)\tau}]\mathrm{d}\tau \\
=\frac{-V_{sn}}{2\hbar}[\frac{e^{i(\omega_{sn}-\omega)t}-1}{\omega_{sn}-\omega}+\frac{e^{i(\omega_{sn}+\omega)t}-1}{\omega_{sn}+\omega}],$$

Since $e^{i\theta}-1=2ie^{i\theta/2}\sin(\theta/2)$, eq. 23 becomes

$$a_s(t)=\frac{-iV_{sn}}{\hbar}[\frac{e^{i(\omega_{sn}-\omega)t/2}\sin[(\omega_{sn}-\omega)t/2]}{\omega_{sn}-\omega}+\frac{e^{i(\omega_{sn}+\omega)t/2}\sin[(\omega_{sn}+\omega)t/2]}{\omega_{sn}+\omega}],$$

The first term in eq. 24 is *absorption* while the second term is called *stimulated emission*.

Notice that the terms in eq. 24 are only significant when $\omega\approx\pm\omega_{sn}$, that is, a matching of the frequency of the harmonic interaction with the transition energy between quantum states (Figure 3).

<p align="center">
<img src="http://Shengxiang-Joey-Wu.github.io/images/blogImages/pinc_Figure3.jpg" width="412">
</p>  

We first analyze the absorption part:

$$P(t)=\vert a_s(t)\vert^2=\frac{\vert V_{sn}\vert^2}{\hbar^2(\omega_{sn}-\omega)^2}\sin^2[\frac{1}{2}(\omega_{sn}-\omega)t],$$

We then do a similar transformation as in eqs. 17-18,

$$P(t)=|V_{sn}|^2\frac{\sin^2[\frac{1}{2}(\omega_{sn}-\omega)\hbar t/\hbar]}{\hbar^2(\omega_{sn}-\omega)^2} \\
=|V_{sn}|^2\frac{\sin^2[\frac{1}{2}\Delta Et/\hbar]}{\Delta E^2} \\
=\frac{2\pi t}{\hbar}|V_{sn}|^2\delta_t(\Delta E) \\
=\frac{2\pi t}{\hbar}|V_{sn}|^2\delta_t(\hbar(\omega_s-\omega_n-\omega)),$$

Note that $\Delta E$ here is defined as $\Delta E\equiv\hbar(\omega_s-\omega_n-\omega)$. The transition rate for this absorption process is therefore

$$R_{\mathrm{abs}}=\frac{\mathrm{d}P(t)}{\mathrm{d}t}=\frac{2\pi}{\hbar}|V_{sn}|^2\delta_t(\hbar(\omega_s-\omega_n-\omega)),$$

Similarly, the transition rate for the stimulated emission process is

$$R=\frac{2\pi}{\hbar}|V_{sn}|^2\delta_t(\hbar(\omega_s-\omega_n+\omega)),$$

The overall transition rate (probability per unit time) from state $n$ to state $s$ is then

$$R=\frac{2\pi}{\hbar}|V_{sn}|^2\delta_t(\hbar(\omega_s-\omega_n-\omega))+\frac{2\pi}{\hbar}|V_{sn}|^2\delta_t(\hbar(\omega_s-\omega_n+\omega)),$$

Note that within the long time limit, we neglect interferences between the resonant and anti-resonant terms.

Furthermore, the Dirac delta function can be expressed in a Lorentzian function form to account for the relaxation process,

$$\delta(\hbar(\omega_s-\omega_n\pm\omega))=\delta(\varepsilon_f-\varepsilon_i\pm\hbar\omega)=\frac{1}{\pi}\lim_{\gamma\rightarrow 0}\frac{\gamma}{(\varepsilon_f-\varepsilon_i\pm\hbar\omega)^2+\gamma^2},$$

Note here that we define that $\hbar\omega_s\equiv\varepsilon_f$ and $\hbar\omega_n\equiv\varepsilon_i$, the subscript $f$ and $i$ simply mean the final and initial states.

By introducing a damping factor $\gamma=\hbar/\tau$ in eq. 30, and substituting eq. 30 in eq. 29 (note that we switched notation here $\vert V_{sn}\vert^2=\vert M_{fi}\vert^2$)

$$R=\frac{2}{\tau}[\frac{\vert M_{fi}\vert^2}{(\varepsilon_f-\varepsilon_i-\hbar\omega)^2+(\hbar/\tau)^2}+\frac{\vert M_{fi}\vert^2}{(\varepsilon_f-\varepsilon_i+\hbar\omega)^2+(\hbar/\tau)^2}],$$

After accounting for the spin and the occupation probability dictated by the Fermi-Dirac distribution, eq. 31 becomes

$$R=\frac{4}{\tau}f(\varepsilon_i)(1-f(\varepsilon_f))[\frac{\vert M_{fi}\vert^2}{(\varepsilon_f-\varepsilon_i-\hbar\omega)^2+(\hbar/\tau)^2}+\frac{\vert M_{fi}\vert^2}{(\varepsilon_f-\varepsilon_i+\hbar\omega)^2+(\hbar/\tau)^2}],$$

If one considers all the possible initial states, eq. 32 would become the eq. 1 in ref. 2.

Wavefunctions of Spherical Nanoparticles
=====

Then we need to find the appropriate basis set for conduction electrons in plasmonic nanoparticles. For simplicity, we consider nanoparticles with a spherical shape, this would leave us a central force problem when solving the $\mathrm{schr\ddot{o}diner}$ equation:

$$\hat{H}=\hat{T}+\hat{V}=-(\frac{\hbar^2}{2m})\nabla^2+V(r),$$

where $\nabla^2\equiv\frac{\partial^2}{\partial x^2}+\frac{\partial^2}{\partial y^2}+\frac{\partial^2}{\partial z^2}$.

For spherical shape, it is convenient to work within the spherical coordinates, so we rewrite the Laplace operator in spherical coordinates,

$$\nabla^2\equiv\frac{\partial^2}{\partial r^2}+\frac{2}{r}\frac{\partial}{\partial r}+\frac{1}{r^2}\frac{\partial^2}{\partial\theta^2}+\frac{1}{r^2}\cot{\theta}\frac{\partial}{\partial\theta}+\frac{1}{r^2\sin^2\theta}\frac{\partial^2}{\partial\phi^2},$$

It can be shown that (in any quantum mechanics/chemistry book) 

$$\hat{L}^2=-\hbar^2(\frac{\partial^2}{\partial\theta^2}+\cot\theta\frac{\partial}{\partial\theta}+\frac{1}{\sin^2{\theta}}\frac{\partial^2}{\partial\phi^2}),$$

where $\hat{L}$ is the angular momentum operator.

Therefore, eq. 33 is transformed to

$$\hat{H}=-\frac{\hbar^2}{2m}(\frac{\partial^2}{\partial r^2}+\frac{2}{r}\frac{\partial}{\partial r})+\frac{1}{2mr^2}\hat{L}^2+V(r),$$

And it can also be shown that 

$$[\hat{H}, \hat{L}^2]=0\qquad \mathrm{if}\;V=V(r) \\

[\hat{H}, \hat{L_z}]=0\qquad\mathrm{if}\;V=V(r),$$

Thus, it is possible to have a set of simultaneous eigenfunctions of $\hat{H}$, $\hat{L}^2$, and $\hat{L}_z$ for the central-force problem,

$$\hat{H}\psi=E\psi;\qquad\hat{L}^2\psi=l(l+1)\hbar^2\psi,\;\;\;l=0,1,2,...\\
\hat{L}_z\psi=m\hbar\psi,\;\;\;m=-l,-l+1,...,l,$$

Using the above eigenvalues, eq. 36 can be transformed as

$$-\frac{\hbar^2}{2m}(\frac{\partial^2\psi}{\partial r^2}+\frac{2}{r}\frac{\partial\psi}{\partial r})+\frac{l(l+1)\hbar^2}{2mr^2}\psi+V(r)\psi=E\psi,$$

The eigenfunctions of $\hat{L}^2$ are spherical harmonics $Y_l^m(\theta, \phi)$, and since $\hat{L}^2$ does not involve $r$, it is possible to multiply $Y_l^m$ by an arbitrary function of $r$ and still have eigenfunctions of $\hat{L}^2$ and $\hat{L}_z$.

$$\psi=R(r)Y_l^m(\theta,\phi),$$

Plug the variable-separated wavefunction in eq. 39 and divide both sides by $Y_l^m$, one may get an ordinary differential equation for the unknown function $R(r)$

$$-\frac{\hbar^2}{2m}(R''+\frac{2}{r}R')+[\frac{l(l+1)\hbar^2}{2mr^2}+V(r)]R=ER,$$

Then we transform eq. 46 a little bit and then enlist mathematical solutions (sometimes a friend majoring in mathematics is a plus),

$$-\frac{\hbar^2}{2m}(R''+\frac{2}{r}R')+[\frac{l(l+1)\hbar^2}{2mr^2}+V(r)]R=ER \\
\Rightarrow -\frac{\hbar^2}{2m}(R''+\frac{2}{r}R')+[(V(r)-E)+\frac{l(l+1)\hbar^2}{2mr^2}]R=0 \\
\Rightarrow R''+\frac{2}{r}R'-[\frac{2m}{\hbar^2}(V(r)-E)+\frac{l(l+1)}{r^2}]R=0 \\
\Rightarrow r^2R''+2rR'-[\frac{2mr^2}{\hbar^2}(V(r)-E)+l(l+1)]R=0 \\
\Rightarrow r^2R''+2rR'+[-\frac{2mr^2}{\hbar^2}(V(r)-E)-l(l+1)]R=0,$$

Try $R$ as $y(x)$ and $x=kr$, $k=\sqrt{\frac{-2m(V(r)-E)}{\hbar^2}}$

$$\frac{dR}{dr}=\frac{dR}{dx}\frac{dx}{dr}=\frac{dy}{dx}\sqrt{\frac{-2m(V(r)-E)}{\hbar^2}}\qquad\frac{d^2R}{dr^2}=\frac{d\frac{dR}{dr}}{dx}\frac{dx}{dr}=\frac{d^2y}{dx^2}\frac{-2m(V(r)-E)}{\hbar^2}$$

Thus, eq. 42 becomes

$$\frac{-2m(V(r)-E)}{\hbar^2}r^2\frac{d^2y}{dx^2}+2r\sqrt{\frac{-2m(V(r)-E)}{\hbar^2}}\frac{dy}{dx}+[-\frac{2mr^2}{\hbar^2}(V(r)-E)-l(l+1)]y=0,$$

Since $x=\sqrt{\frac{-2m(V(r)-E)}{\hbar^2}}r$, the above equation becomes

$$x^2\frac{d^2y}{dx^2}+2x\frac{dy}{dx}+(x^2-l(l+1))y=0,$$

It turns out that eq. 45 has analytical solutions: the two linearly independent solutions are spherical Bessel functions of the first kind $j_l$ and spherical Bessel functions of the second kind $y_l$.

$$j_l(x)=(-x)^l(\frac{1}{x}\frac{d}{dx})^l\frac{\sin{x}}{x},\qquad y_l(x)=-(-x)^l(\frac{1}{x}\frac{d}{dx})^l\frac{\cos{x}}{x},$$

***
**Finite spherical potential well**

Instead of considering infinite potential well as we usually did in quantum chemistry textbooks, here we consider a more realistic scenario (Figure 4), that is, the potential inside the spherical nanoparticles has a finite value $V_0$, and the potential outside the nanoparticle is $0$ (vacuum level).

<p align="center">
<img src="http://Shengxiang-Joey-Wu.github.io/images/blogImages/pinc_Figure4.jpg" width="400">
</p>  

It is noted that in this scenario, $V_0$ is a negative value. And from eq. 46, one may write down the wavefunction inside the nano-sphere, which is $\psi_\mathrm{in}=j_l(kr)$ and $k=\sqrt{\frac{2m(E-V_0)}{\hbar^2}}$. Since the potential outside the sphere is $0$, the wavefunction is $\psi_\mathrm{out}=h_l(\kappa r)$ with $\kappa=\sqrt{\frac{2mE}{\hbar^2}}$. $h_l(x)$ is called the spherical Hankel function of the first kind, and it is defined as $h_l(x)=j_l(x)+iy_l(x)$.

Alternatively, the wavefunctions outside the nano-sphere can also be viewed as the modified spherical Bessel function of the second kind, $k_l(\kappa r)$, and $\kappa=\sqrt{\frac{-2mE}{\hbar^2}}$. Note the argument difference in the spherical Hankel function of the first kind and the modified spherical Bessel function of the second kind. We will use the latter as our wavefunction outside the nano-sphere since it is purely real. 

Then we need to apply boundary conditions to find eigenenergies: the wavefunction needs to be continuous and smooth. Continuous requires that wavefunctions converge on the surface of the nano-sphere, while smooth requires the first derivatives of wavefunctions also converge on the surface.

$$\mathrm{Continuous:\qquad\psi_\mathrm{in}=\psi_\mathrm{out}}\bigg\rvert_{r=r_0};\qquad \mathrm{Smooth: \frac{d\psi_\mathrm{in}}{dr}}=\frac{d\psi_\mathrm{out}}{dr}\bigg\rvert_{r=r_0},$$

Rather than finding the cross points for the above conditions separately, the logarithmic derivative is used instead

$$\frac{\frac{d\psi_\mathrm{in}}{dr}}{\psi_\mathrm{in}}=\frac{\frac{d\psi_\mathrm{out}}{dr}}{\psi_\mathrm{out}}\bigg\rvert_{r=r_0},$$

which reads

$$k\frac{j_l'(kr)}{j_l(kr)}\bigg\rvert_{r=r_0}-\kappa\frac{k_l'(\kappa r)}{k_l(\kappa r)}\bigg\rvert_{r=r_0}=0,$$

Then the allowed energy (implicitly included in $k$ and $\kappa$) can be found by searching roots of eq. 49. We could repeat this procedure for all possible $l$, and Figure 5a summarized these results. Furthermore, we can also visualize the convoluted density of states (DOS) as shown in Figure 5b, it matches well with the three-dimensional free-electron-gas models in solid-state physics as expected.

<p align="center">
<img src="http://Shengxiang-Joey-Wu.github.io/images/blogImages/pinc_Figure5.jpg" width="683">
</p>  

The parameter $V_0$ is crucial since it determines the material's work function. For $D=15\;\mathrm{nm}$ Ag nano-sphere, we choose $V_0=-10.04\;\mathrm{eV}$ to ensure the correct work function ($~4.5\;\mathrm{eV}$).  For a wavefunction to be well-behaved, we require it to be normalized, $\int_{-\infty}^\infty \psi^*\psi\mathrm{d}\tau=1$. After normalization, we can pick three random state wavefunctions (Figure 6) to visualize that the boundary conditions are fulfilled. As shown in Figure 6, the found wavefunctions are indeed continuous and smooth across the interface (solid line for inside the sphere, and dashed line for outside the sphere).

<p align="center">
<img src="http://Shengxiang-Joey-Wu.github.io/images/blogImages/pinc_Figure6.jpg" width="420">
</p>  

Nonthermal Carrier Generation
=====

Now we have all the tools we need to calculate the generation rate and energy distribution of nonthermal carriers - we have equipped with the formula derived from the Fermi-Golden rule and the wavefunctions to describe the conduction band electrons in nanospheres. By looking at eq. 32, we realize the only remaining puzzle is the transition matrix element $M_{fi}=\langle\psi_f\vert eV'\vert\psi_i\rangle$, where $V'$ is the **overall** potential that electrons feel when the illumination is on. The overall potential for spherical nanospheres can be written as $V'=V_{ext}+V_p$, where $V_{ext}$ is the external potential and $V_p$ is the plasmon-induced potential, the latter can be written as (from entry-level electromagnetics books):

$$V_p(r,\omega)=\begin{cases} \frac{\varepsilon-1}{\varepsilon+2}E_0r\cos\theta\qquad\mathrm{inside\;sphere}\\\frac{\varepsilon-1}{\varepsilon+2}\frac{R^3}{r^2}E_0\cos\theta\qquad\mathrm{outside\;sphere}\end{cases},$$

And the external perturbation is simply $V_{ext}=-E_0r\cos\theta$. For silver, we use the Drude model $\varepsilon=\varepsilon_b-\frac{\omega_{pl}^2}{\omega^2+\mathrm{i}\omega\gamma}$ with background dielectric function $\varepsilon_\mathrm{b}=4.18$, a plasma frequency $\omega_{pl}=9.07\;\mathrm{eV}$, and a plasmon damping of $\gamma=60\;\mathrm{meV}$.<sup>2</sup> 

One more trick to note here, the transition matrix element is evaluated below

$$\vert \langle\psi_f\vert V'\vert\psi_i\rangle\vert^2=e^2E_0^2\vert\langle R_f\vert V'(r)\vert R_i\rangle\vert ^2\vert \langle Y_{l_f}^{m_f}\vert\cos\theta\vert Y_{l_i}^{m_i}\rangle\vert^2,$$

Luckily, we do not need to deal with the explicit expression: it turns out that $\vert\langle Y_{l_f}^{m_f}\vert\cos\theta\vert Y_{l_i}^{m_i}\rangle\vert^2$ can be evaluated analytically as

$$\vert\langle Y_{l_f}^{m_f}|\cos\theta|Y_{l_i}^{m_i}\rangle|^2=2\frac{(l_\mathrm{min}-m+1)(l_\mathrm{min}+m+1)}{(2l_\mathrm{min}+3)(2l_\mathrm{min}+1)},$$

where $l_\mathrm{min}$ is the smaller value between $l_f$ and $l_i$. Note the selection rule is that $l_f-l_i=\pm 1$ and $m_f=m_i$.

**Finally**, we can put everything together and evaluate the transition probability per unit time (equivalently, the excitation rate) using eq. 32 (Figure 7). For comparison, we also put the results from ref. 2 side by side. 

<p align="center">
<img src="http://Shengxiang-Joey-Wu.github.io/images/blogImages/pinc_Figure7.jpg" width="611">
</p>  

If you are interested in the detailed MATLAB code to perform this calculation, please email me at shengxiangwu996@gmail.com.



**References**
1. Khurgin, J. B. How to deal with the loss in plasmonics and metamaterials. *Nat Nanotechnol* **2015**, *10* (1), 2-6.
2. Manjavacas, A.; Liu, J. G.; Kulkarni, V.; Nordlander, P. Plasmon-Induced Hot Carriers in Metallic Nanoparticles. *ACS Nano* **2014**, *8* (8), 7630-7638.
3. Govorov, A. O.; Zhang, H.; Gun’ko, Y. K. Theory of Photoinjection of Hot Plasmonic Carriers from Metal Nanostructures into Semiconductors and Surface Molecules. *The Journal of Physical Chemistry C* **2013**, *117* (32), 16616-16631.
4. Sundararaman, R.; Narang, P.; Jermyn, A. S.; Goddard Iii, W. A.; Atwater, H. A. Theoretical predictions for hot-carrier generation from surface plasmon decay. *Nature Communications* **2014**, *5* (1), 5788.
5. Brown, A. M.; Sundararaman, R.; Narang, P.; Goddard, W. A., 3rd; Atwater, H. A. Nonradiative Plasmon Decay and Hot Carrier Dynamics: Effects of Phonons, Surfaces, and Geometry. *ACS Nano* **2016**, *10* (1), 957-966.
6. Wu, S.; Sheldon, M. T. Optical Power Conversion via Tunneling of Plasmonic Hot Carriers. *ACS Photonics* **2018**, *5* (6), 2516-2523.
7. Wu, S.; Chen, Y.; Gao, S. Plasmonic Photocatalysis with Nonthermalized Hot Carriers. *Physical Review Letters* **2022**, *129* (8), 086801.


