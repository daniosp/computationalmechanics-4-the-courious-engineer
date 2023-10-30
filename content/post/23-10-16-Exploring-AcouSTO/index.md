---
title: Exploring AcouSTO, a Numerical Solver for acoustics.
date: 2023-10-16
image: 
  focal_point: 'top'
  caption: "From AcouSTO ‘s official website -  [https://acousto.sourceforge.net/](https://acousto.sourceforge.net/)"
share: false
---

<p align="justify">
As a Mechanical Engineering student, I was searching for an approach to acoustics when I came across AcouSTO - an open-source software. It was presented to me as a great alternative to learning about the complex science of sound wave propagation. Additionally, the <a href="https://nicoguaro.github.io/pages/about/">professor</a> who introduced me to the software also suggested to share my findings in the form of a blog post. Thus, this project was born. AcouSTO's computing capabilities will be the starting point of our discussion. Let's clarify what they are.
</p>

<!--more-->

***
# ¿What is AcouSTO? 
***

<p align="justify">
AcouSTO is an open-source software for acoustic simulation released in 2009. The project was developed as a Boundary Element Method (BEM) solver for the Kirchhoff-Helmholtz Integral Equation (KHIE) within domains of arbitrary geometry. Although many open-source software alternatives for the simulation of multiple physics phenomena were available at the time, AcouSTO emerged as an acoustic-centered solution capable of handling interior and exterior problems whilst being a relatively simple tool for the average experienced user. 
</p>
<p align="justify">
If you are unfamiliar with the Boundary Element Method, in essence, it is a numerical technique used in computational mechanics to solve problems in which the solution depends only on the boundary of the domain, rather than the entire domain itself. This method is applied in fields such as heat transfer, fluid dynamics, electromagnetism, and, in particular, problems involving boundary surfaces.  Let’s take an example of a situation on heat transfer to clarify what the main idea behind the method is:
</p>
<p align="justify">
Imagine you have an irregularly shaped metal plate, and you want to understand how heat is distributed across its surface. Instead of dividing the plate into tiny pieces, as you might in the Finite Element Method (FEM), the BEM concentrates on the edges or boundaries of the plate. The method works by dividing these edges into small, manageable segments (usually flat elements). Then, it calculates the properties, like temperature in this case, at these boundary segments. With this information, BEM uses mathematical integral equations to relate the values at one segment to the values at neighboring segments considering the physical behavior that governs the manner in which a physical quantity, like temperature, should spread over the boundary. After solving for the information around the boundary, the integral equations can be reapplied to compute the numerical solution at any point within the solution domain. In the case of our example, this would refer to the heat distribution on the surface of the metal plate.
</p>
<p align="justify">
The Boundary Element Method becomes especially helpful in acoustic problem-solving as the interest of the problem rests on the scattering of waves around geometric surfaces. Integral equations describe the relationship between the acoustic field and the boundary conditions, yielding solutions on the boundary. What’s more, AcouSTO allows the configuration of “microphones” at any location in the analyzed domain to obtain values at desired points of interest. In general, AcouSTO offers two categories of problem-solving as detailed in the User Manual:</p>

* Scattering of planar or spherical waves by multiple, arbitrarily shaped, bodies ;
* Radiation of vibrating closed surfaces with wall motion assigned.

{{% callout note %}}
🌐 [Check out AcouSTO ’s official website!](https://acousto.sourceforge.net/)
{{% /callout %}}

***
# AcouSTO ‘s features and limitations
***

<p align="justify">
Upon reviewing the official website and the User Manual, I noticed several important features and limitations of the software. Here is a list of them, in no particular order:
</p>

* AcouSTO can solve problems governed by Laplace, Poisson, and Helmholtz Equations.
* Runs in parallel on MPI2 clusters (MPICH or OpenMPI).
* Pre- and post-processing with [Gmsh](http://geuz.org/gmsh/), [Paraview](http://www.paraview.org/), and [Blender](http://www.blender.org/).
* Easy installation via GNU build system (Linux and OSX) or [Docker](http://www.docker.com/) image.
* [Windows 10 Linux Subsystem](https://msdn.microsoft.com/it-it/commandline/wsl/install_guide) compatible.
* The use of the KHIE for the analysis of the radiation and scattering of a closed surface {{< math >}}$S${{< /math >}} within the free space is affected by the so–called fictitious _eigenfrequencies_ problem. This problem causes the scattered acoustic field in the surrounding unbounded domain to display non-physical resonances that are related to the _eigensolutions_ of the interior problem. To address this issue, AcouSTO provides an option to regularize the BEM exterior solution using the CHIEF technique (Combined Helmholtz Integral Equation Formulation). However, this approach has a drawback as it reduces reliability at high frequencies or for frequencies corresponding to a high modal density range for the enclosure bounded by {{< math >}}$S${{< /math >}}.
* The current version of AcouSTO can handle only isolated monopoles and incoming plane waves. There are currently no limits on the number of monopoles or incoming plane waves that can be configured for a problem.
* The current version of the code is unable to handle surfaces or sources that move.

***
# Resources
***
Iemma, U. & Marchese, V. (2017). AcouSTO User’s Manual v2.0. https://acousto.sourceforge.net/UserManual.pdf
