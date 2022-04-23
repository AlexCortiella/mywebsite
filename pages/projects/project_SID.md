---
layout: current-project
permalink: /current-project/
---

# Overview
The project focuses on nonlinear system identification, the aim of which is to identify and understand a physical system from noisy measurements and predict its behavior. Specifically, the main goal is to recover the governing equations of an unknown system via sparse regularized regression methods. 

![Current research](/assets/images/images_projects/SID_Dynamics.jpg){:class="img-markdown"}

# Motivation
Engineering relies heavily on mathematical models of real systems. In the design process, engineers seek the best models that describe the physical system they want to design and optimize. However, physical processes are often highly complex and not entirely understood, so the modeling of the first principles can be challenging, sometimes even impossible. System identification is the science of extracting a model from a set of observations or measurements. By looking at how a system behaves in specific situations, we can determine whether there are patterns in the behavior and what factors influence it.

# Method
The approach used to recover the governing equations of the unknown system is based on regression with additional constraints promoting simplicity of the resulting model. We assume that the governing equations can be expressed as linear combinations of nonlinear candidate functions weighted by constant coefficients and only few of the nonlinear functions contribute to the system dynamics. The \\(\ell_1\\)-norm is used as a regularization constraint to select which of the candidate functions are most relevant to the dynamics.

# Publications

* [Cortiella, Alexandre, Kwang-Chun Park, and Alireza Doostan. "Sparse identification of nonlinear dynamical systems via reweighted ℓ1-regularized least squares." Computer Methods in Applied Mechanics and Engineering 376 (2021): 113620.](https://www.sciencedirect.com/science/article/pii/S0045782520308057?casa_token=NvEljYT4iZUAAAAA:6BeLBQRNFrH0f4OWdm80-AGSH_QG2-8YTwdDySdQ6OTlX8SXwNmCmYYKYvsHFolIhIjnR2oRUA "Link to article")

* [Cortiella, Alexandre, Kwang-Chun Park, and Alireza Doostan. "A Priori Denoising Strategies for Sparse Identification of Nonlinear Dynamical Systems: A Comparative Study." arXiv preprint arXiv:2201.12683 (2022).](https://arxiv.org/abs/2201.12683 "Link to preprint")




