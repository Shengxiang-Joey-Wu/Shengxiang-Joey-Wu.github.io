---
title: 'Numerical Modeling of Mie Scattering'
date: 2023-07-01
permalink: /posts/2023/07/numerical_modeling-of-mie-scattering/
excerpt: <img src="http://ShengxiangWuPlasmonic.github.io/images/blogImages/nmoms_TOC.jpg" width="591">
tags:
  - COMSOL Multiphysics
  - Finite Element Method
  - Finite-Difference Time-Domain Method
---

After I chose plasmonic nanoparticles (NPs) as my research field back in 2015, the first thing my advisor asked me to do was to reproduce the Mie scattering of gold NPs using Lumerical FDTD, a numerical solver developed by Lumerical Inc., which was acquired by Ansys in the year (2020) of my graduation. It was the first time I realized the power of modeling or simulation. Since then I have enjoyed comparing things, e.g., comparing theory with experiment, comparing different theories or methods, etc. Now I have been an experienced user of Lumerical FDTD (sorry Ansys, I still prefer to call it Lumerical FDTD) for more than 7 years. I have also been modeling nanophotonics problems with COMSOL Multiphysics, another popular numerical solver, for a long time, yet I still think it is a great exercise to look at this problem, namely, Mie scattering of plasmonic nanoparticles, the phenomenon that makes plasmonic NPs colorful and interesting in nanophotonics and photocatalytic domains. In this blog, I will walk you through the modeling process and we will compare our modeling result with the analytical solution - Mie theory.

Mie theory
=====

Mie theory is an exact analytic solution to Maxwell's equations for spheres with an arbitrary size and thus can be used to calculate the optical spectra, which essentially is an electromagnetic problem, of spherical particles, given that the dielectric constants of the particle and the environment are known. Rather than go through the development and derivation of Mie theory, which I believe deserves another blog, let's take its solution for granted for now and keep in mind that it is an analytical approach.

The general expression for the scattering and extinction cross-sections from Mie theory are 

$$\sigma_\mathrm{sca}=\frac{2\pi R^2}{x^2}\sum_{n=1}^\infty(2n+1){|a_n|^2+|b_n|^2},$$

$$\sigma_\mathrm{ext}=\frac{2\pi R^2}{x^2}\sum_{n=1}^\infty(2n+1)Re[a_n+b_n],$$

where $x=2\pi Rn_\mathrm{m}/\lambda$, $n_\mathrm{m}$ is the refractive index of the medium, $R$ is the radius of the particle, and the absorption cross-section is given by $\sigma_\mathrm{abs}=\sigma_{ext}-\sigma_{sca}$. The $a_n$ and $b_n$ factors are given by

$$a_n=\frac{\psi'(mx)\psi_n(x)-m\psi_n(mx)\psi_n'(x)}{\psi'_n(mx)\zeta_n(x)-m\psi_n(mx)\zeta'_n(x)},$$

$$b_n=\frac{m\psi'_n(mx)\psi_n(x)-\psi_n(mx)\psi'_n(x)}{m\psi'_n(mx)\zeta_n(x)-\psi_n(mx)\zeta'_n(x)},$$

where $\psi_n(z)=(\pi z/2)^{1/2}\times J_{n+1/2}(z)$, $\zeta_n(z)=(\pi z/2)^{1/2}\times(J_{n+1/2}(z)-iY_{n+1/2}(z))$ and $m=n_p/n_m$, where $n_p$ is the refractive index of the particle.The different terms in eqs 1 and 2 correspond to the dipole ($n=1$), quadrupole ($n=2$), and so on. Don't be intimidated if the expression of $\psi_n$ and $\zeta_n$ are complex and not familiar to you, they are just special functions (spherical Bessel and Hankel functions of the first kind) and they are usually built-in functions in scientific computing languages, e.g. MATLAB.

You may wonder what if the shape of nanoparticles is not a sphere? What if the shape is complicated enough that finding an analytical solution is impractical? Well, thanks to the development of applied mathematics, we now have a general solution - the numerical approach. In fact, the numerical methods, such as the *finite-difference time-domain* (FDTD) method, *finite element* (FEM) method, and discrete dipole approximation (DDA), etc., for electromagnetic problems have led to a subject called **computational electromagnetics**. In the following sections, we will use Lumerical FDTD, as the name suggested, is a solver based on the FDTD method, and COMSOL Multiphysics, which is a FEM solver, to model the scattering phenomenon from gold nanoparticles. Since we also have the exact analytic solution, it doesn't hurt to compare the numerical results with it. So, let's go!

Finite-Difference Time-Domain method simulation in Lumerical FDTD
====

The Finite-Difference Time-Domain method is a direct space method, first introduced by Yee in 1966. It solves the time-domain form of Faraday's law and Ampere-Maxwell's law (eqs. 5 and 6)to obtain the time evolution of electric and magnetic fields across a spatial grid (Yee grid cell).

$$\mu\frac{\partial\mathbf{H}}{\partial t}=-\nabla\times\mathbf{E}-\mathbf{M},$$

$$\varepsilon\frac{\partial\mathbf{E}}{\partial t}=\nabla\times\mathbf{H}-\mathbf{J_s}-\sigma\mathbf{E},$$

in which $\mathbf{E}$ is the electric field, $\mathbf{H}$ is the magnetic field, $\mathbf{J_s}$ is the electric current density source and $\mathbf{M}$ is the equivalent magnetic current density. Also, note that we have three primary constitutive parameters of materials to describe the electromagnetic properties:

$$\mathbf{D}=\varepsilon_0\mathbf{E}+\mathbf{P}$$

$$\mathbf{B}=\mu_0(\mathbf{H}+\mathbf{M})$$

$$\mathbf{J}=\sigma\mathbf{E}$$

in which $\varepsilon$ is the electric permittivity, $\mu$ is the magnetic permeability and $\sigma$ represents the conductivity. 

Materials and objects of interest are generally placed into the Yee grids (Figure 1) and assigned constitutive material parameters based on the cell location. [Central differencing](https://en.wikipedia.org/wiki/Finite_difference) is then used to approximate the time and spatial partial derivatives in eqs. 5 and 6. Truncating the Taylor series expansions of the field components yields a second-order accurate scheme in both space and time, which can then be converted into frequency or wavelength domain through the Fourier transform.

<p align="center">
<img src="http://ShengxiangWuPlasmonic.github.io/images/blogImages/nmoms_Figure1.jpg" width="410">
</p>

Since we are interested in the absorption and scattering of electromagnetic waves by spherical nanoparticles, we need to introduce a source in our simulation. There are numerous source options for an FDTD model, hard, soft, resistive voltage, and plane wave sources. In our case, we select plane waves as our source, and in particular, we will model the plane waves from a distant source using the total-field scattered-field formulation.

$$\mathbf{E}=\mathbf{E}_\mathrm{total}=\mathbf{E}_\mathrm{background}+\mathbf{E}_\mathrm{scattered},$$

It turns out that this special plane wave source is a built-in source in the Lumerical FDTD - the *TFSF* source (Figure 2).

<p align="center">
<img src="http://ShengxiangWuPlasmonic.github.io/images/blogImages/nmoms_Figure2.jpg" width="551">
</p>

In addition to the objects (materials), grids, and sources, we need appropriate **boundary conditions** in any numerical simulation. For instance, *perfect electric conductor* (PEC) and *perfect magnetic conductor* (PMC) reflect electromagnetic waves and can be very useful to take advantage of certain types of symmetries in simulation. *Periodic boundary conditions* (PBCs), such as Bloch boundary conditions, are useful when modeling periodic structures, e.g., metasurfaces. And *absorbing* or *radiation boundary conditions* are suitable for open-region problems to avoid infinity simulation regions and to minimize spurious reflections along the outer boundaries of the grid. Among many absorbing boundary conditions, the **perfectly matched layer** (PML) is the most popular one because of its overall efficiency and robustness, and we will use it in our Mie scattering simulation. And guess what, the PML boundary conditions are the default boundary conditions once we add an FDTD region in Lumerical FDTD.

It should be noted that usually one or several dependent variables are solved in any numerical solver, for instance, we solve for $\mathbf{E}$ and $\mathbf{E}$ in Lumerical FDTD, it is then our job to connect the dependent variables to the quantities we want - the cross-sections in Mie scattering. Since the cross-sections are defined as the ratio of power (either absorbed or scattered, unit: $\mathrm{W}$) to input power density (unit: $\mathrm{W/m^2}$), and the input power density is a parameter we can control in the simulation, we just need to know the absorbed or scattered power. We can make the connection between dependent variables $\mathbf{E}$ & \mathbf{H}$ to power through Poynting vectors:

$$P=\int\int(\mathbf{n}\cdot\mathbf{S})dS,$$

where $$P$$ is power, $\mathbf{n}$ is the normal vector of the surface under study, $\mathbf{S}=\mathbf{E}\times\mathbf{H}$ is the Poynting vector, and $dS$ is the surface element. Let's assume the input power density is $I_0$, then the cross-sections are calculated as:

$$\sigma=\frac{P}{I_0}=\frac{1}{I_0}\int\int(\mathbf{n}\cdot\mathbf{S})dS,$$

Seems complicated? Don't worry, it turns out that Lumerical FDTD has many built-in functions and even analysis groups to help us out. For instance, the ```transmission``` script command can be applied to a power monitor (an object we can place in Lumerical FDTD) to get the amount of power transmitted through it. And the built-in **Cross section** analysis group consists of 6 power monitors enclosing a region and analyzing the net power flowing into or out from that enclosed region (Figure 3). Note that for absorption the output cross-section is a negative quantity but it is just due to the convention used in Lumerical FDTD. So it becomes that we just need to put one cross section analysis group inside the TFSF soruce to capture the absorption cross-section, and put another outside the TFSF source, where only the scattered field is present (Figure 2), to calculate the scattering cross-section.

<p align="center">
<img src="http://ShengxiangWuPlasmonic.github.io/images/blogImages/nmoms_Figure3.jpg" width="537">
</p>

Therefore, the procedures for setting up Lumerical FDTD simulation for Mie scatterings are:

1. Set up simulation region (**Simulation** $\rightarrow$ **Add FDTD region**), and note that the outer boundary of the simulation region has defaulted to PML layers. So make sure the simulation region is large enough  so the evanescent tails of the resonant surface plasmon modes will not interact with the PML boundary conditions.
2. Put a gold nanosphere at the center of the simulation **(Structures** $\rightarrow$ **Sphere**) and edit its radius as you want. Make sure to change the material to Au.
3. Put a TFSF source (**Sources** $\rightarrow$ **Total-field scattered-field**) enclosing the gold nanoparticles . Set the wavelength from 400 nm to 700 nm, this wavelength range is suitable to capture the localized surface plasmon resonance of gold nanospheres.
4. Insert a Cross section analysis group (from **Analysis** $\rightarrow$ **Optical power** $\rightarrow$ **Cross section**) inside the TFSF source, and edit its dimension to enclose the gold nanoparticles. This analysis group will calculate the absorption cross-section.
5. Insert another Cross section analysis group to enclose the TFSF source. This analysis group will calculate the scattering cross-section.
6. If one needs higher accuracy, one can override the mesh setting by inserting a user-defined mesh (**Simulation** $\rightarrow$ **Mesh**).
7. You may also want to modify the wavelength or frequency data points so you can get a nice-looking spectrum. You can do this in **Monitors** $\rightarrow$ **Global properties**.

By following the steps above, we should be able to get the simulation files looking like [these], which I have set up and finished the simulation for gold nanospheres with radii of 30 nm and 80 nm.  And the result can be viewed by right-clicking the cross section analysis groups (**Run analysis**, and then **Visualize**). There is one more thing that I didn’t tell you yet about the optical constant I used in the simulation, I will touch on that after we discussed COMSOL Multiphysics. 

Finite Element Method Simulation in COMSOL Multiphysics
=====

The finite element method (FEM) is another numerical method that is used to solve boundary-value problems characterized by a partial differential equation and a set of boundary conditions. It is a more universal method compared with the finite-difference time-domain method, and thus can also be applied to other physics governed by other partial differential equations, such as heat transfer, stress analysis, mass diffusion, etc. In FEM, the geometrical domain of the boundary-value problem, for instance, the gold nanosphere and its surroundings in our case, is discretized using sub-domain elements, called the _finite elements_, and the differential equation is applied to a single element after it is brought to the _weak form_. Then a set of shape functions (also known as _interpolation functions_) is used to represent the primary unknown variable, e.g., the electric field $\mathbf{E}$, in the element domain. A set of linear equations is obtained for each element in the discretized domain. Finally, a global matrix system is formed after the assembly of all elements.

Before we dive into the modeling process in COMSOL Multiphysics, let’s look at a one-dimensional problem of electrostatics (Figure 4) to get a better understanding of FEM. As shown in Figure 4, we are curious about the spatial profile of electric potential $V$ between two parallel conducting plates separated by a distance $d$. And the left plate is maintained at a fixed potential $V =V_0$, while the right plate is grounded $V_n = 0\;\mathrm{V}$. The subscript $n$ is due to we divide the geometry into $n$ segments. To complete the physical picture, let’s say the medium between the two plates is nonmagnetic with a dielectric constant $\varepsilon_r$ and a uniform electron volume charge density $\rho_v=-\rho_0$ is also present in the medium.

<p align="center">
<img src="http://ShengxiangWuPlasmonic.github.io/images/blogImages/nmoms_Figure4.jpg" width="467">
</p>

The (partial) differential equation associated with the above problem is Poisson’s equation:

$$\nabla(\varepsilon_r\nabla V)=-\frac{\rho_v}{\varepsilon_0},$$

Since the medium between the two plates is homogeneous, linear, and isotropic, the above equation can be converted into 

$$\frac{d^2V}{dx^2}=\frac{\rho_0}{\varepsilon_r\varepsilon_0},$$

In FEM, briefly, we need to find solutions that satisfy the governing partial differential equation at each node, and then one may use linear interpolation to find approximate solutions between two nodes. Two common approaches for finding solutions at nodes are the variational approach and the method of weighted residual. Instead of going through every detail of FEM, let’s use the method of weighted residual as an example to demonstrate what is the weak form in the FEM. 

The solution inside the $e^{th}$ element can be written as 

$$V=\sum_{j=1}^nv_j^eN_j(x),$$


