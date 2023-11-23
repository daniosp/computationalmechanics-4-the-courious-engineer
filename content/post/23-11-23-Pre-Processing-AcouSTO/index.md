---
title: "Scattering of a spherical wave by a rigid sphere [Part 1]: Understanding AcouSTO’ s pre-processing configuration"
date: 2023-11-23
image: 
  focal_point: 'top'
share: false
---

<p align="justify">
Now that AcouSTO is installed on our computer, we are ready to use it. Our first approach to the program will be the exercise found in Chapter 1 of the Book of Tutorials. This problem consists of the scattering of a spherical wave by a rigid sphere. Although the mathematical background of the analytical solution will be presented, the main focus of this post is to share a tutorial on the essential use of AcouSTO through the analysis of the structure of the configuration file.
</p>

<!--more-->

***
## A (not so thorough) presentation of the analytical solution
***

<p align="justify">
The problem that we will be solving consists of the scattering of a sound wave around a rigid sphere. The source of the sound wave, which is located at a distance {{< math >}}$r_s${{< math >}} from the origin {{< math >}}$O${{< math >}}, is a monopole of unit amplitude. This means that the source is simplified as a point in space that radiates sound equally in all directions.  The propagating sound wave will interact with the surface of a rigid sphere of radius {{< math >}}$a${{< math >}}, whose center is coincident with the origin.  The problem has an axisymmetric behavior w.r.t. the axis that includes both the origin and the source location, therefore the complete solution for the whole field can be obtained by solving the problem for an arbitrary plane passing through the symmetry axis. The formulation of the problem within a generic plane can be written in polar coordinates; where the source would be located at {{< math >}}$\mathbf{r_s}=(r_s,\theta)${{< math >}}. 
</p>



<p align="justify">
Now that we have a clear formulation of the situation let’s continue by reviewing the governing equations of the acoustic problem. However, before we dive any further into mathematics, I must make a disclaimer. The math behind the solution to this problem can be somewhat complicated for a student who is just learning the basics of acoustics. Based on that reasoning, I will explain the main equations used by the software to solve the acoustic problem and clarify the meaning of its terms in a more beginner-friendly manner. 
</p>


<p align="justify">
AcouSTO solves for the velocity potential {{< math >}}$(\phi)${{< math >}} function of an acoustic field, which in this case  is written as:
</p>

{{< math >}} 
$$
\nabla^2\phi + k^2
\phi = \delta(\mathbf{r} - \mathbf{r_s}), \text{ with    } \frac{\partial\phi}{\partial r} = 0 \text{ for } r = a \tag1
$$ 
{{< math >}}

<p align="justify">
On the left side of the equation, {{< math >}}$\nabla^2\phi + k^2
\phi${{< math >}}, refers to the mathematical description of the behavior of waves that propagate through a fluid medium (like air). Here, the term {{< math >}}$k= \frac{\omega}{c_0}${{< math >}} is known as the wavenumber, which is a parameter that indicates the number of radians a wave changes per meter. On the other side of the equation, we have the expression {{< math >}}$\delta(\mathbf{r} - \mathbf{r_s})${{< math >}}, which in mathematics is called the Dirac delta function. This function denotes an instantaneous impulse that occurs at a concentrated point in space and produces a sudden perturbation of the medium. In the studied scenario, equaling both expressions together means that we will solve for the potential velocity of the sound wave produced by the monopole. The additional comment, {{< math >}}$\frac{\partial\phi}{\partial r} = 0 \text{ for } r = a${{< math >}}, indicates that the velocity potential around the boundary, or surface, of the rigid sphere will be constant. This is true for this particular problem, where the condition of axial symmetry is satisfied.
</p>

<p align="justify">
The solution to equation {{< math >}}$(1)${{< math >}} can be written, in polar coordinates, as follows:
</p>

{{< math >}} 
$$
\phi(r,\theta)=\phi_{inc}+\phi_{sc}=-\frac{e^{ikR}}{4 \pi R}+\frac{ik}{2\pi}\sum_{n=0}^{\infty}{\left( n+\frac{1}{2} \right) \frac{j'_n(ka)h_n(kr_s)}{h'_n(ka)}}h_n(kr)P_n(\cos\theta) \tag2
$$
{{< math >}} 

<p align="justify">
This equation is used to calculate the potential velocity measured at a circle formed by 100 microphones positioned at a distance {{< math >}} $r_{mics}=1.5a${{< math >}} . Some of the terms within the equation may seem complex, hence, to provide a better understanding, a list containing their explanations is presented below:
</p>

<ol>
  <li>{{< math >}} $\phi_{inc}${{< math >}}  and {{< math >}} $\phi_{sc}${{< math >}} : Velocity potential of the incident and scattered field, respectively. The incident field refers to the velocity potential solution for a domain where no obstacle or interference is present. On the other hand, the scattered field delivers information regarding how the sound wave deviates from its original behavior once it encounters objects or boundaries.</li>

 <li>{{< math >}}$h_n(kr)${{< math >}} and {{< math >}}$(kr)${{< math >}}: Hankel and Bessel functions of the first kind. Mathematical functions used in acoustics and wave physics to describe the radial components of spherical waves.</li>

 <li>{{< math >}}$P_n(x)${{< math >}}: Legrende polynomial of order $n$. Refers to a mathematical expression used for solving Helmholtz’s equation (equation {{< math >}}$(1)${{< math >}}).</li>

 <li>{{< math >}}$R=||\mathbf{r-r_s}||${{< math >}}: Indicates the magnitude of the distance distance between an arbitrary point in space, {{< math >}}$\mathbf{r}=(r,\theta)${{< math >}}, and the point where the source is located, {{< math >}}$\mathbf{r_s}=(r_s,0)${{< math >}}.</li>

</ol>

<p align="justify">
We will solve the acoustic problem for the given values {{< math >}}$a=1${{< math >}} and {{< math >}}$r_s=3${{< math >}}. In the following section, we will discuss how the main configuration file is set up to solve the problem correctly with the use of AcouSTO.
</p>


***
## Understanding the main configuration file
***

<p align="justify">
The files needed for the tutorial are located under the path:
</p>

```Docker
~/acousto-1.6b/doc/tutorials/Sphere_Monopole$
```
<p align="justify">
For this first approach to AcouSTO, we’ll only be using the following files:
</p>

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-fymr{border-color:inherit;font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-fymr">File name</th>
    <th class="tg-fymr">Content</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky"><span style="font-style:italic">sphere_source.cfg</span></td>
    <td class="tg-0pky">Main configuration file for setting up AcouSTO 's solver.</td>
  </tr>
  <tr>
    <td class="tg-0pky"><span style="font-style:italic">acousto.sources</span></td>
    <td class="tg-0pky">Location and intensity of the sound source.</td>
  </tr>
  <tr>
    <td class="tg-0pky"><span style="font-style:italic">acousto.mics1.5.mesh</span></td>
    <td class="tg-0pky">Coordinate placement for the circle of microphones.</td>
  </tr>
</tbody>
</table>

<p align="justify">
AcouSTO 's configuration files consist of modular code blocks. The blocks contain the parameter values for the many variables that the program has to consider when solving an acoustic simulation. Below, we will analyze the meaning behind the most important parameters of each of the blocks contained within the sphere_source.cfg configuration file.
</p>

* <strong><em>runinfo</em> block:</strong>
<p align="justify">
This block contains the general parameters and information about the code execution.
</p>

```c++
runinfo={
 active = 1; 
 title = "custom-title";   // Title of the current code execution
 owner = "name";           // Username of the person who runs the code
 ksymmi=24;                // Symmetry flag
 krow  =-1;                // Number of matrix rows to be loaded in RAM
 vsound  =343.0;           // Speed of sound, 343 m/s for standard air
};
```
<p align="justify">
The parameter ksymmi becomes particularly important for this problem as it indicates the number of symmetric slices that the solver will handle. Later it will be shown that the value of this parameter is consistent with the configuration of the geometry. For axis-symmetrical problems, the parameter has values {{< math >}}$N>3${{< math >}}, where {{< math >}}$N${{< math >}} refers to the number of partitions of the geometry.  On the other hand, the krow flag controls memory allocation in RAM. When the value of this parameter is set to krow {{< math >}}$\le 0${{< math >}}, like in this case, it indicates to AcouSTO that the number of matrixes to be loaded in RAM is equal to the total number of control points of the geometry. 
</p>

***
# Resources
***
Iemma, U. & Marchese, V. (2017). 