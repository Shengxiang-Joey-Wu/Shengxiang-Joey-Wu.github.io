---
title: 'Cyclic Voltammetry in Electrochemistry'
date: 2022-09-24
permalink: /posts/2022/09/cyclic-voltammetry-in-electrochemistry/
excerpt: <img src="http://Shengxiang-Joey-Wu.github.io/images/blogImages/cvie_TOC.jpg" width="728">
tags:
  - Cyclic Voltammetry
  - Electrochemistry
---

There was always a cyclic voltammetry (CV) running on the lab computer (remotely controlled by my colleagues) every time I passed by. I got really curious about the CV map, especially why there are two $y$ (current) values corresponding to one $x$ (potential) value. What got me more curious is that my colleagues can show each other the CV map and talk science about it. I was too shy to ask how they do it (don't be like me), so I decided to figure it out myself, not only because I was curious but also if I wanted to perform photoelectrochemistry experiments on plasmonic nanoparticles someday, I gotta know how the CV works and what it can tell me. So I am writing this blog to educate myself:


Preliminary Knowledge
======

***
**chemical equilibrium**

For a simple chemical reaction

$$A\rightleftarrows B$$

The equilibrium constant is defined as $K=\frac{[B]}{[A]}$, and once the equilibrium is reached the concentrations $[A]$ and $[B]$ do not change with time.

**kinetics**

At equilibrium, however, it does not mean that the reaction is 'frozen' - it is just because the forward reaction rate $v_f$ equals the backward reaction rate $v_b$ so the concentration of reactants and products does not change over time. Assuming the forward and backward reactions are both first-order reactions, then the reaction rates and the equilibrium condition can be written as:

$$v_f =k_f[A],\qquad v_b=k_b[B],$$

$$v_f=v_b\Rightarrow k_f[A]=k_b[B],$$

where the $k_f$ and $k_b$ are the rate constants of forward and backward reactions, respectively. Both equilibrium constant (thermodynamic concept) and kinetics are important as the former tells us what equilibrium looks like and the latter tells us how fast we can get there.

**activation energy and the Arrhenius equation** 

In most cases, there is a 'hill' that reactant A needs to surpass before forming product B even if the reaction is energetic favorable $(\Delta_rG<0)$. The peak of the 'hill' is usually represented by a transition state (TS) or activated complex, and we can therefore define activation energies for forward $(E_{a,f})$ and backward $(E_{a,b})$. reactions. This is the basis of the transition state theory (Figure 1).

<p align="center">
<img src="http://Shengxiang-Joey-Wu.github.io/images/blogImages/cvie_Figure1.jpg" width="329">
</p>

[The Arrhenius equation](https://en.wikipedia.org/wiki/Arrhenius_equation) states that the rate constant is related to the activation energy and absolute temperature through

$$k=Ae^{\frac{-E_a}{RT}}$$

where $A$ is a pre-exponential factor, it contains everything that we don't know (lol) about rate constant and ideally it should be temperature-insensitive. One can imagine that the rate constant would be greater (the reaction is faster) if activation energy is smaller (or temperature is higher) if other reaction parameters are kept the same.

**the Nernst equation**

The potential of a redox $(\mathrm{Ox}/\mathrm{Red})$ couple is characterized by the [Nernst equation](https://en.wikipedia.org/wiki/Nernst_equation), which links the potential to the concentration of $\mathrm{Ox}$ and $\mathrm{Red}$ species. The Nernst equation in the general case is:

$$\mathrm{Ox}+n\mathrm{e^-}\rightleftarrows \mathrm{Red},$$

$$E=E^0+\frac{RT}{nF}\ln\frac{C_\mathrm{Ox}}{C_\mathrm{Red}},$$

where $C_\mathrm{Ox}$ and $C_\mathrm{Red}$ are the concentrationsa of $\mathrm{Ox}$ and $\mathrm{Red}$ species. The potential evaluated in the Nernst equation is also a thermodynamics property, but it turns out also affecting the reaction rates through the transition state theory (Figure 1): the ratio between $\mathrm{Ox}$ and $\mathrm{Red}$ species alters the relative position of $\mathrm{Ox}$ (A) and $\mathrm{Red}$ (B) in the potential energy surface (PES), therefore, it also alters the activation energies felt by $\mathrm{Ox}$ and $\mathrm{Red}$ (will be explained in detail below). 

***

The above preliminary knowledge shall leave us on the same page and can be found in many undergraduate chemistry textbooks. Now, we started to derive the cyclic voltammetry.<sup>1-3</sup>

Electron Transfer Process (A General Description)
=====

Since the redox reactions involve electron transfer, it wouldn't hurt if we first study the electron transfer process in general (Figure 2). The simplest scenario is the one-electron transfer process that reduces $\mathrm{Ox_1}$ to its reductive form $\mathrm{Red_1}$.

$$\mathrm{Ox_1}+\mathrm{e^-}\rightarrow \mathrm{Red_1}$$

Imagine we are electrons, why sometimes do we flow from A to B and sometimes from B to A? What is the driving force behind that? Well, simply put, we always want to flow to somewhere we feel more comfortable (low potential energy). This is universal regardless if it is a homogeneous electron transfer or heterogeneous electron transfer (Figure 2): To reduce $\mathrm{Ox_1}$ to $\mathrm{Red_1}$, the electrons may be injected from another reducing agent $\mathrm{Red_2}$ where the electrons are more uncomfortable (high potential energy) or from an electrode that is purposely maintained at the high (negative) potential.

<p align="center">
<img src="http://Shengxiang-Joey-Wu.github.io/images/blogImages/cvie_Figure2.jpg" width="542">
</p>

At this stage, it is important for us to keep this in mind: 1) electrons tend to flow from high energy to low energy, 2) for electrodes, positive potential tends to lower electron energy (electrons are more comfortable), thus preventing electrons flowing out from electrode, and *vice versa*.

Diffusion In An Electrochemical Cell
=====

Now we are ready to see what my colleagues usually do in the lab: constructing an electrochemical (EC) cell and performing analysis such as CV. A representative EC cell (3-electrode configuration) is shown in Figure 3. As the name suggests, it contains three electrodes: the working electrode is the one we are primarily interested in as it drives the targeted redox reactions (either the electrolyte or the electrode itself), the counter electrode is just for circuit connection purposes (it can extract or inject electrons to electrolyte solutions easily), and the reference electrode tells us what is the potential now of working electrode, that is, when reporting potential we usually write *vs. reference electrode*.  

<p align="center">
<img src="http://Shengxiang-Joey-Wu.github.io/images/blogImages/cvie_Figure3.jpg" width="663">
</p>

There is one key difference between an EC cell and an ordinary electric circuit: the current measured in an EC cell is dictated by the reaction rates of oxidation of $\mathrm{Red}$ (inject electrons to the electrode) and reduction of $\mathrm{Ox}$ (extract electrons from the electrode) occurred on the electrode surface, while the current measured in an ordinary electric circuit is determined by the voltage drop and the resistance (Ohm's law). In an EC cell, therefore, the currents depend on the reaction rates, which are further related to the concentrations of Ox and Red species and the potential provided by the working electrode (see below). What's important is that besides the reactions that consume or produce redox couples, both Ox and Red are suffered from diffusion in the EC cell (see inset in Figure 3).

If, for simplicity, we treat the diffusion in one dimension only, that is, we assume both $\mathrm{Ox}$ and $\mathrm{Red}$ only diffuse perpendicular to the electrode surface and the electrode surface is perfectly smooth, then we can use [the Fick's second law of diffusion](https://en.wikipedia.org/wiki/Fick%27s_laws_of_diffusion) (eq. 8) to describe the diffusion of $\mathrm{Ox}$ and $\mathrm{Red}$ out from and approach to the surface.

$$\frac{\delta C}{\delta t}=D\frac{\delta^2 C}{\delta x^2},$$

where $D$ is the diffusion coefficient. The direction of diffusion is from high concentration to low concentration.

Applied Potential Modifies Activation Energy
=====
There is one significant question remaining, that is, how does the applied electric potential alter the PES (or equivalently, the reaction coordinates)? To illustrate this, we can consider a reduction process in which the reactant is the $\mathrm{Ox}+\mathrm{e}^-$ (assume it is a one-electron, one-step process) and the electrons are from the working electrode. As we went through together that positive potential tends to lower electron energy while negative potential raises the energy up, we can plot three scenarios in Figure 4, wherein the applied electric potential is referenced to the standard (or formal) potential $E^0$ of the redox couple under consideration.

<p align="center">
<img src="http://Shengxiang-Joey-Wu.github.io/images/blogImages/cvie_Figure4.jpg" width="672">
</p>

To avoid confusion, I have replaced activation energy $E_a$ with the free energy of activation $\Delta G$ (they are the same thing here), and the subscript $c$ and $a$ stands for cathode (where reduction happens) and anode (where oxidation happens), respectively. It is shown in the lower left and middle panel in Figure 4, that if the potential is changed by $\Delta E>0$ to a new value, the relative energy of the electron resident on the electrode changes by $-F\Delta E=-F(E-E^0)$; hence the $\mathrm{Ox}+\mathrm{e^-}$ curve moves down by that amount. Apparently (I hate this word), the barrier for reduction, $\Delta G_c$, has become greater than $\Delta G_c^0$, and the barrier for oxidation, $\Delta G_a$ has become less than $\Delta G_a^0$ by a fraction of the total energy change. Let us call that fraction $1-\alpha$, where $\alpha$, the *transfer coefficient*, can range from zero to unity.<sup>2</sup>

Therefore, we have the following two expressions for the activation energies for anodic and cathodic barriers:

$$\Delta G_a=\Delta G_a^0-(1-\alpha)F(E-E^0),$$

$$\Delta G_c=\Delta G_c^0+\alpha F(E-E^0),$$

If we assume the rate constants $k_f$ and $k_b$ have the Arrhenius form, we have

$$k_f=A_fe^{-\Delta G_c/RT}=A_fe^{-\Delta G_c^0/RT}e^{-\alpha F(E-E^0)}=k_f^0e^{-\alpha F(E-E^0)}=k^0e^{-\alpha F(E-E^0)},$$

$$k_b=A_be^{-\Delta G_a/RT}=A_be^{-\Delta G_a^0/RT}e^{(1-\alpha) F(E-E^0)}=k_b^0e^{(1-\alpha) F(E-E^0)}=k^0e^{(1-\alpha) F(E-E^0)},$$

The last $^"=^"$ in the above two equations is simply because $E^0$ can be chosen at the formal potential of the interested redox pair, which gives $k_f^0=k_b^0=k^0$.

Final Step: The Point Method
=====

Now we have everything we need to know to evaluate the current (the $y$ values) in a CV measurement. However, evaluating the diffusion using eq. 8 turns out to be difficult, we then use the point method<sup>3</sup> to evaluate diffusion in the discrete form:

$$\frac{C_j-C_i}{\Delta t}=\frac{D[C_{i-1}-2C_i+C_{i+1}]}{\Delta_x^2}$$

$$C_j=C_i+\lambda(C_{i-1}-2C_i+C_{i+1})$$

where $\lambda=D\Delta t/\Delta x^2$, and the distance (measured from the electrode surface) and time increments, $\Delta x$ and $\Delta t$, are originated from the point method (Figure 5a). In Figure 5b, we display the potential sweep in one cycle during CV measurement: the working electrode's potential is swept from a high potential to a low potential (or *vice versa*), and then back to its original value. The CV measurement gets its name since during the potential sweep, the current due to redox reactions is measured simultaneously.

<p align="center">
<img src="http://Shengxiang-Joey-Wu.github.io/images/blogImages/cvie_Figure5.jpg" width="765">
</p>

The first column represents the concentration at the electrode surface, which are calculated values discussed below. The boundary conditions are applied in order to use the point method: 1) the last column contains concentrations furthest from the electrode surface and is thus filled with the bulk concentration. The top row of the grid contains concentration values at the start of the simulation, and it is filled with the bulk concentration as well. Equation 14 is then used to fill the rest of the grid (it should be combined with consumption or production due to redox reactions, otherwise there will be no diffusion and you will fill the grid with bulk conditions everywhere).

Result and Discussion
=====

We are almost there, I promise. We now can work out the diffusion in its discrete form, but we need to bear in mind that the redox reactions also modify the concentration of $\mathrm{Ox}$ and $\mathrm{Red}$ at the electrode surface, and the redox current is the one my colleagues record in the CV measurement. In this sense, the redox reactions caused the concentration gradient at the electrode surface, and drove the diffusion: 

$$J_\mathrm{Ox}=-D[C_\mathrm{Ox,1}-C_\mathrm{Ox,0}]/\Delta x$$ 

where $J$ is the current density, this equation describes that if the electrode consumes the $\mathrm{Ox}$ and then the diffusion of $\mathrm{Ox}$ occurs toward the electrode. Unfortunately, this equation cannot be used directly in the simulation because the concentration of the $\mathrm{Ox}$ at the electrode surface $(C_\mathrm{Ox,0})$ is still unknown. However, this equation can be arranged to $C_\mathrm{Ox,0}=C_\mathrm{Ox,1}+(J_\mathrm{Ox}\Delta x/D)$. Similarly, $C_\mathrm{Red,0}=C_\mathrm{Red,1}+(J_\mathrm{Red}\Delta x/D)$. Furthermore, since the flux of the oxidized form can also be written as a rate equation $(J_\mathrm{Ox}=k_fC_\mathrm{Ox,0}-k_bC_\mathrm{Red,0})$, and the substitution of the two previous equations into the rate equation, one can reach

$$-J_\mathrm{Ox}=\frac{k_fC_\mathrm{Ox,1}-k_bC_\mathrm{Red,1}}{1+\frac{k_f\Delta x}{D}+\frac{k_b\Delta x}{D}}$$

$$J_\mathrm{OX}=-J_\mathrm{Red}$$

where $k_f$ and $k_b$ are obtained from eqs. 11 and 12 at each applied potential. The total faradaic current that corresponds to each time increment is finally calculated as:

$$i_\mathrm{Total}=-nFAJ_\mathrm{Ox}$$

where $A$ is the active area of the electrode. One more thing to note: aside from the diffusion we now have the equations that describe the modification of concentrations at the electrode surface:

$$C_\mathrm{Ox,0}=C_\mathrm{Ox,1}+\frac{J_\mathrm{Ox}\Delta x}{D}$$

$$C_\mathrm{Red,0}=C_\mathrm{Red,1}+\frac{J_\mathrm{Red}\Delta x}{D}$$

The eqs. 19 and 20, along with eq. 14 dictates the whole concentration profile from the electrode surface to the bulk solution.

The algorithm is therefore as follows: 1) use eq. 16 to calculate the current density (the $y$ values in CV measurement), 2) use eqs. 14, 19, and 20 to update concentration profiles (after $\Delta t$), 3) repeat steps 1 and 2 until the sweep cycle is finished. A typical simulated CV map is shown in Figure 6, along with the concentration profiles of $\mathrm{Ox}$ and $\mathrm{Red}$. [Download sample MATLAB code here](https://github.com/Shengxiang-Joey-Wu/Shengxiang-Joey-Wu.github.io/raw/refs/heads/main/files/Cyclic_Voltammetry_Simulation.zip)

<p align="center">
<img src="http://Shengxiang-Joey-Wu.github.io/images/blogImages/cvie_Figure6.jpg" width="750">
</p>

Remember what gets us here? Why there are two $y$ values for one $x$ value? Now we have the answer: it is not like an ordinary circuit where the potential (and resistance) dictates current. In a CV measurement, the current originates from the redox reactions at the electrode surface, its sign depends on the type of reaction (oxidation or reduction), and its magnitude depends on the reaction rate. Therefore, the potential itself is just one parameter that controls the reaction type and rate, other parameters such as the initial condition in the EC cell, diffusion, etc, also play important roles in determining reaction rates and thus can result in two current values for a single potential value.

References
=====
1. Noémie Elgrishi, Kelley J. Rountree, Brian D. McCarthy, Eric S. Rountree, Thomas T. Eisenhart, and Jillian L. Dempsey, *Journal of Chemical Education* **2018** *95* (2), 197-206.
2. Bard, A. J.;  Faulkner, L. R.; White, H. S., *Electrochemical methods: fundamentals and applications*. John Wiley & Sons: 2022.
3. Jay H. Brown, *Journal of Chemical Education* **2015** *92* (9), 1490-1496.

