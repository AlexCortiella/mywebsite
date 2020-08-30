---
layout: post
subheadline: 3D Rotations
title:  'Orientation in three-dimensional space: Attitude representations'
teaser: "Understanding orientation in 3D space is fundamental for scientists and engineers. How would it be possible to control an aircraft, rocket or spacecraft without defining their orientation precisely? Unlike the 2D case, description of orientations in space becomes involved and harder to visualize. The purpose of this post is to introduce different ways to describe orientations in space and make complicated concepts easier to understand through basic math and animations."

publicationdate: June 11, 2020
update: June 11, 2020
author: Alexandre Cortiella
categories: Education
topic: Attitude representations
featured: yes
tags: featured
image: 
  header: /assets/images/images_blog/Attitude_representations/Orientation3D_cover.jpg
  thumb: /assets/images/images_blog/Attitude_representations/gimbal_thumb.jpg
  caption: Photo by AUTHOR
  caption_url: link to pic author
---

**Note:** This post requires some basic knowledge of linear algebra and vector calculus.

## Introduction 

I stumbled upon the realm of rotational dynamics when I was working on the attitude determination and control system of a small satellite a few years back. At first, it was a bit daunting because I had never worked in attitude dynamics before and I only had basic knowledge from my undergraduate courses. However, I started to learn from books and put everything in practice. Finally, I ended up loving this field, and I would like to do my bit by sharing one of the concepts that fascinates me: orientation (or attitude) and rotational dynamics of rigid bodies in three-dimensional space. Understanding and describing how an object is oriented in space is crucial for aerospace applications: from maneuvering aircraft and spacecraft to describe the attitude dynamics of asteroids or other orbiting bodies. 

The motion of particles, bodies or system of bodies without considering the agents that cause them to move is often referred as *kinematics*. The motion of any body  in a three-dimensional space can be described by six *parameters*, also known as *degrees of freedom* (dof) which are divided in three translational dofs and three rotational dofs. On the one hand, the "position" of a body is often described by the "x", "y" and "z" Cartesian coordinates. On the other hand, the orientation or "attitude" of a body can be expressed by three different "angles". However, these are not the only ways to describe position and attitude. The focus of this post is to explain the different representations one can use to describe the orientation of a body. 

**Notation**: In this post I will refer to vectors as $$\vec{\mathbf{v}}$$ where its components in a specific *reference frame* as the column matrix $$\mathbf{v}$$. Vectors with unit norm will be written with a hat symbol $$\hat{\mathbf{v}}$$. For matrices, I will use a bold, uppercase letter $$\mathbf{A}$$ if they are two dimensional and bold, lowercase letter $$\mathbf{a}$$ if they are one dimensional (that is, column matrices).

<figure style = "text-align: center">
<img class = "equation-wrapper" src="/assets/images/images_blog/Attitude_representations/equation_1.svg">
</figure>

where each component $$b_{ij}$$ is simply the orthogonal projection of $$\mathbf{b}_i$$ onto each basis vector $$\mathbf{a}_j$$. For the second component, for example, $$b_{12} = \hat{\mathbf{b}}_1\cdot\hat{\mathbf{a}}_2 = \|\hat{\mathbf{b}}_1\| \|\hat{\mathbf{a}}_2\| \text{cos}(\alpha_{12})$$. Since both $$\hat{\mathbf{b}}_1$$ and $$\hat{\mathbf{a}}_2$$ have unit norm, the projection of $$\hat{\mathbf{b}}_1$$ onto $$\hat{\mathbf{a}}_2$$ is simply the cosine of the angle formed by the basis vectors. If we repeat this process for all basis vectors of $$\mathcal{B}$$, we should obtain

<figure style = "text-align: center">
  <img src="/assets/images/images_blog/Attitude_representations/3d_reference_frames.jpg" width="70%">
  <figcaption style = "text-align: justify"><small><strong>Figure 1:</strong> Direction cosines of reference frame B reltaive to A.</small></figcaption>
</figure>

