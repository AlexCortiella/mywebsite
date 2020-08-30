---
layout: project_TopOpt
permalink: /project_TopOpt/
---


# Overview

This project, concluded in my B.S. thesis, was concerned with the optimization of an aircraft wing rib structure subject to aerodynamic pressure loads. Topology Optimization (TO) techniques were employed to perform such task. In few words, Topology optimization (TO) is a mathematical method that optimizes material layout within a given design space, for a given set of loads, boundary conditions and constraints with the goal of maximizing the performance of the system. In this project, we used Finite Element Analysis along with constrained nonlinear optimization techniques to maximize the compliance of the struture subject to mass constraints.

<figure style = "text-align: center">
  <img src="/assets/images/images_projects/topology_optimization_example.png" width="60%">
  <figcaption style = "text-align: center"><small><strong>Figure 1:</strong> Structural topology optimization concept.</small></figcaption>
</figure>

# Motivation 

Structural optimization (S.O.) has become a popular tool in engineering because it usually shortens the decision making process and leads to an overall cost reduction of structural engineering projects. Optimization is crucial in an environment in which companies strive to convince customers that their products are the best. In recent years, structural optimization tools have been increasingly accepted in automotive, aerospace or other related industries for structural design processes. One of the main advantages that make S.O. an essential tool nowadays is the fact that it has redefined the concept design phase of structural components.

In aerospace industry it is important to optimize the design of a structure so as to make it as lightweight as possible ensuring safety requirements. A weight reduction implies savings in material costs, less fuel consumption and less environmental damage. Nowadays, S.O. tools have become popular and increasingly supported by the aerospace industry.

# Method

The goal of this proect was to optimize the internal structure of a wing rib structure subject to aerodynamic loads using Finite Element Analysis (FEA) and Topology optimization techniques. Wing ribs are forming elements of the framework of a wing that give the aerodynamic shape of the cross section of a wing as well as structural rigidity. The optimization process is shown below.

<figure style = "text-align: center">
  <img src="/assets/images/images_projects/TopOpt_WingRib.jpg" width="70%">
  <figcaption style = "text-align: center"><small><strong>Figure 2:</strong> Optimization process of an aircraft wing rib.</small></figcaption>
</figure>

The main question of the thesis was: Given a specific aerodynamic profile, aerodynamic loads and boundary conditions, how can we remove material, and thus reduce weight, in an optimal way maximizing the stiffness of the structure? To answer this question we used density-based structural topology optimization -- the SIMP method specifically -- as well as the Method of Moving Assymptotes (MMA) to solve a non-convex optimization problem. THe idea was to divide the wing rib into a irregular grid formed by small elements and iteratively remove those elements in a smart way to reduce the overall weight.

Optimization of the leading edge of the wing rib

<video class = "blog_video" autoplay loop muted playsinline width="70%">
    <source type="video/webm" src="/assets/images/images_projects/LEdgeTO.webm">
</video>
<figcaption style = "text-align: center"><small><strong>Animation 1:</strong> Topology optimization of the leading edge of the rib.</small></figcaption>

Optimization of the central component of the wing rib

<video class = "blog_video" autoplay loop muted playsinline width="70%">
    <source type="video/webm" src="/assets/images/images_projects/WBoxTO.webm">
</video>
<figcaption style = "text-align: center"><small><strong>Animation 2:</strong> Topology optimization of the central region of the rib.</small></figcaption>

Optimization of the trailing edge of the wing rib

<video class = "blog_video" autoplay loop muted playsinline width="70%">
    <source type="video/webm" src="/assets/images/images_projects/TEdgeTO.webm">
</video>
<figcaption style = "text-align: center"><small><strong>Animation 3:</strong> Topology optimization of the trailing edge of the rib.</small></figcaption>

# More info

* Here you can download my thesis and appendices in PDF: [Download Thesis](\assets\downloads\BS_THESIS_MEMORY.pdf) / [Download Appedices](assets\downloads\BS_THESIS_APPENDICES.pdf)


* For recent advances in topology optimization in mechanics I highly recommend the research conducted by [Dr. Kurt Maute's lab](https://www.colorado.edu/center/aerospacemechanics/research/multi-physics-design-optimization) at CU Boulder and the projects at the [International Centre for Numerical Methods in Engineering (CIMNE)](https://www.cimne.com/).