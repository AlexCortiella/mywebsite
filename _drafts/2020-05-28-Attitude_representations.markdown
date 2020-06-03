---
layout: post
subheadline: 3D Rotations
title:  'Orientation in three-dimensional space: Attitude representations'
teaser: "SpaceX is trying to revolutionize the internet communications sector by launching a megaconstellation of thousands of small satellites, called Starlink. With state-of-the-art satellite internet technology, and a global network unbounded by ground infrastructure limitations, Starlink will deliver high speed broadband internet to locations where access has been unreliable, expensive, or completely unavailable. How will Starlink make this possible?"

publicationdate: May 25, 2020
update: May 25, 2020
author: Alexandre Cortiella
categories: Education
topic: Attitude kinematics
featured: yes
tags: featured
image: 
  header: /assets/images/images_blog/starlink_project/starlink-cover.jpg
  thumb: /assets/images/images_blog/starlink_project/Starlink_thumb_high.jpg
  caption: Photo by AUTHOR
  caption_url: link to pic author
---

**Disclaimer:** This post requires some basic knowledge of linear algebra and vector calculus.

## Introduction 

This post will cover one of the concepts that fascinates me the most: orientation (a.k.a attitude) and rotational dynamics of rigid bodies in three-dimensional space. Understanding and describing how an object is oriented in space is crucial for aerospace applications: from maneuvering aircraft and spacecraft to describe the attitude dynamics of asteroid or other orbiting bodies. 

The motion of a points, bodies or system of bodies without considering the agents that cause them to move is often referred as "kinematics". The motion of any body  in a three-dimensional space can be described by six "parameters", also known as "degrees of freedom (dof)" which are divided in three translational dofs and three rotational dofs. On the one hand, the "position" of a body is often described by the "x", "y" and "z" Cartesian coordinates. On the other hand, the orientation or "attitude" of a body can be expressed by three different "angles". However, these are not the only ways to describe position and attitude. In two dimensions, only three dofs are needed to describe the motion of an object.


The first step to describe the orientation of a body in space is by introducing the concept of reference frame. A frame of reference consists of a set of three orthogonal unit vectors (axis) $$\{\mathbf{e}_1, \mathbf{e}_2, \mathbf{e}_3\}$$ and an origin $$\mathcal{O}$$ that fixes those axis to a certain location in space. If we wanted to describe the position of a body, we would use the set $$\{\mathbf{O},\mathbf{e}_1, \mathbf{e}_2, \mathbf{e}_3\}$$, but since we are interested in the orientation we will drop the origin and assume all vectors are referenced to it. The reference frame $$\mathcal{O}$$ is then defined as $$\mathcal{O}:\{\mathbf{e}_1, \mathbf{e}_2, \mathbf{e}_3\}$$. Once the reference frame is defined, we can express any vector in that frame as
 
$$\mathbf{v} = v_1\mathbf{e}_1 + v_2\mathbf{e}_2 + v_3\mathbf{e}_3,$$

where $$\{v_1, v_2, v_3\}_{\mathcal{O}}$$ are the coordinates of $$\mathbf{v}$$ in the reference frame $$\mathcal{O}$$. Note that the coordinates are the orthogonal projections of $$\mathbf{v}$$ onto each basis vector $$\mathbf{e}_i$$ (i.e. $$v_i = \mathbf{v}\cdot\mathbf{e}_i,\quad i = 1,2,3.$$). 

To define the attitude of an object we must always have in mind that the orientation is a relative concept. One defines the orientation of an object **relative to a reference frame**. Thus we must employ two reference frames, one attached to the object and another one that will be used to describe the orientation with respect to it. Let us define two reference frames defined by their orthogonal basis vectors as $$\mathcal{A}: \{\mathbf{a}_1, \mathbf{a}_2, \mathbf{a}_3\}$$ and $$\mathcal{B}: \{\mathbf{b}_1, \mathbf{b}_2, \mathbf{b}_3\}$$. The goal is to represent the attitude of $$\mathcal{B}$$ relative to $$\mathcal{A}$$. There are many attitude representations to achieve this goal. In this post I will focus on four of them: direction cosine matrix (DCM), axis-angle representation, Euler angles and quaternions.

## Direction Cosine Matrix (DCM)

The direction cosine matrix is the most fundamental of all attitude representations and the one we will first study.

The direction cosine matrix allows us to express the basis vectors of one reference frame in terms of the basis vectors of a different one by means of the angles formed by them. We will call $$\alpha_{ij}$$ the angle that goes from basis vector $$j$$ of $$\mathcal{A}$$ to basis vector $$i$$ of $$\mathcal{B}$$. Let us start by expressing $$\mathbf{b}_1$$ in terms of $$\mathbf{a}_1, \mathbf{a}_2, \mathbf{a}_3$$. As discussed before, any vector can be expressed in a reference frame as

$$\mathbf{b}_1 = b_{11}\mathbf{a}_1 + b_{12}\mathbf{a}_2 + b_{13}\mathbf{a}_3$$

where each component $$b_{ij}$$ is simply the orthogonal projection of onto each basis vector $$\mathbf{a}_j$$. Thus, for the second component, for example, $$b_{12} = \mathbf{b}_1\cdot\mathbf{a}_2 = \|\mathbf{b}_1\| \|\mathbf{a}_2\| cos(\alpha_{12})$$. Since both $$\mathbf{b}_1$$ and $$\mathbf{a}_2$$ have unit norm, the projection of $$\mathbf{b}_1$$ onto $$\mathbf{a}_2$$ is simply the cosine of the angle formed by the basis vectors. If we repeat this process for all basis vectors of $$\mathcal{B}$$, we should obtain

$$\mathbf{b}_1 = cos(\alpha_{11})\mathbf{a}_1 + cos(\alpha_{12})\mathbf{a}_2 + cos(\alpha_{13})\mathbf{a}_3$$

$$\mathbf{b}_2 = cos(\alpha_{21})\mathbf{a}_1 + cos(\alpha_{22})\mathbf{a}_2 + cos(\alpha_{23})\mathbf{a}_3$$

$$\mathbf{b}_3 = cos(\alpha_{31})\mathbf{a}_1 + cos(\alpha_{32})\mathbf{a}_2 + cos(\alpha_{33})\mathbf{a}_3$$

<figure style = "text-align: center">
  <img src="/assets/images/images_blog/Attitude_representations/3d_reference_frames.jpg" width="70%">
  <figcaption style = "text-align: justify"><small><strong>Figure 2:</strong> Direction cosines of reference frame B reltaive to A.</small></figcaption>
</figure>

For convenience, we can stack the basis vectors as rows of a matrix, called "vectrix", and express the relations above as 

$$\{\mathcal{B}\} = \begin{bmatrix}\mathbf{b}_1\\\mathbf{b}_2\\\mathbf{b}_3\end{bmatrix} = \begin{bmatrix}cos(\alpha_{11}) & cos(\alpha_{12}) & cos(\alpha_{13})\\cos(\alpha_{21}) & cos(\alpha_{22}) & cos(\alpha_{23})\\cos(\alpha_{31}) & cos(\alpha_{32}) & cos(\alpha_{33})\end{bmatrix}\begin{bmatrix}\mathbf{a}_1\\\mathbf{a}_2\\\mathbf{a}_3\end{bmatrix} = \mathbf{C}_{\mathcal{A}}^{\mathcal{B}}\begin{bmatrix}\mathbf{a}_1\\\mathbf{a}_2\\\mathbf{a}_3\end{bmatrix} = \mathbf{C}_{\mathcal{A}}^{\mathcal{B}}\{\mathcal{A}\}$$

where $$\mathbf{C}_{\mathcal{A}}^{\mathcal{B}}$$ is the direction cosine matrix (DCM). Because each set of basis vectors of $$\mathcal{A}$$
and $$\mathcal{B}$$ consists of orthogonal unit vectors, the direction cosine matrix $$\mathbf{C}_{\mathcal{A}}^{\mathcal{B}}$$ is an
orthonormal matrix; thus, we have 

$${\mathbf{C}_{\mathcal{A}}^{\mathcal{B}}}^T = {\mathbf{C}_{\mathcal{A}}^{\mathcal{B}}}^{-1}$$

Hence, the inverse relation from reference frame $$\mathcal{B}$$ to $$\mathcal{A}$$ is then 

$$\{\mathcal{A}\} = {\mathbf{C}_{\mathcal{B}}^{\mathcal{A}}}\{\mathcal{B}\} = {\mathbf{C}_{\mathcal{A}}^{\mathcal{B}}}^{-1}\{\mathcal{B}\} = {\mathbf{C}_{\mathcal{A}}^{\mathcal{B}}}^{T}\{\mathcal{B}\}$$.

Now, using the above relations, we are able to express the set of coordinates (or components) of any vector given in a reference frame into another set of coordinates given in a different reference frame. Let us express a general vector $$\mathbf{v}$$ in reference frames $$\mathcal{A}$$ and $$\mathcal{B}$$ as

Reference frame $$\mathcal{A}: \mathbf{v} = v_1 \mathbf{a}_1 + v_2 \mathbf{a}_2 + v_3 \mathbf{a}_3$$

Reference frame $$\mathcal{B}: \mathbf{v} = v_1' \mathbf{b}_1 + v_2' \mathbf{b}_2 + v_3' \mathbf{b}_3$$

Note that $$v_i$$ and $$v_i'$$ are **different** coordinates (numbers). Let us project the vector $$\mathbf{v}$$ onto the basis vector of the reference frame $$\mathcal{B}$$.

$$\mathbf{b}_1\cdot\mathbf{v} = v_1' = v_1 \mathbf{b}_1\cdot\mathbf{a}_1 + v_2 \mathbf{b}_1\cdot\mathbf{a}_2 + v_3 \mathbf{b}_1\cdot\mathbf{a}_3$$

$$\mathbf{b}_2\cdot\mathbf{v} = v_2' = v_1 \mathbf{b}_2\cdot\mathbf{a}_1 + v_2 \mathbf{b}_2\cdot\mathbf{a}_2 + v_3 \mathbf{b}_2\cdot\mathbf{a}_3$$

$$\mathbf{b}_3\cdot\mathbf{v} = v_3' = v_1 \mathbf{b}_3\cdot\mathbf{a}_1 + v_2 \mathbf{b}_3\cdot\mathbf{a}_2 + v_3 \mathbf{b}_3\cdot\mathbf{a}_3$$

Writing the coordinates in a column array and since $$\mathbf{b}_i\cdot\mathbf{a}_j = cos(\alpha_{ij})$$, we can now relate the coordinates of a vector in the reference frame $$\mathcal{A}$$ into $$\mathcal{B}$$ as 

$$\mathbf{v}_{\mathcal{B}} = \mathbf{C}_{\mathcal{A}}^{\mathcal{B}}\mathbf{v}_{\mathcal{A}}$$

where $$\mathbf{v}_{\mathcal{B}} = [v_1', v_2', v_3']^T$$ and $$\mathbf{v}_{\mathcal{A}} = [v_1, v_2, v_3]^T$$. It is important to understand that a vector does not depend on a reference frame, but the coordinates with respect to a reference frame do! Look at figure X, the vector $$\mathbf{v}$$ remains the same, but its coordinates with respect to reference frame $$\mathcal{A}$$ and $$\mathcal{B}$$ are different.

<figure style = "text-align: center">
  <img src="/assets/images/images_blog/Attitude_representations/2d_reference_frames.jpg" width="70%">
  <figcaption style = "text-align: justify"><small><strong>Figure 2:</strong> Coordinates of a 2D vector in two different reference frames.</small></figcaption>
</figure>

Hey Alex! Did you say that you only need three parameters or coordinates to represent the attitude of a reference frame relative to another, right? If so, why do we have 9 coefficient in the DCM? Yes, you are totally right! However those 9 coefficients are not idependent. Do you remember that the DCM matrix is orthonormal? Let us take a deeper look. So we have $${\mathbf{C}_{\mathcal{A}}^{\mathcal{B}}}^T = {\mathbf{C}_{\mathcal{A}}^{\mathcal{B}}}^{-1}$$. If we multiply by $$\mathbf{C}_{\mathcal{A}}^{\mathcal{B}}$$ on both sides, we get

$$\mathbf{C}_{\mathcal{A}}^{\mathcal{B}}{\mathbf{C}_{\mathcal{A}}^{\mathcal{B}}}^T = \mathbf{I}$$

where $$\mathbf{I}$$ is the identity matrix. So if we equate all the coefficients after performing the matrix multiplication on the RHS we get 9 relationhips. Let us look at the terms on the diagonal. After equating boths sides, we get

$$cos(\alpha_{11})^2 + cos(\alpha_{12})^2 + cos(\alpha_{13})^2 = 1$$

$$cos(\alpha_{21})^2 + cos(\alpha_{22})^2 + cos(\alpha_{23})^2 = 1$$

$$cos(\alpha_{31})^2 + cos(\alpha_{32})^2 + cos(\alpha_{33})^2 = 1$$

Does these relationships tell you anything? Yes, they are saying something that we did know already. They say that the norm of each basis vector of a reference frame should be 1! Note that the angles $$\alpha_{ij}$$ are the projections of the basis vectors of $$\mathcal{B}$$ onto $$\mathcal{A}$$. Therefore, these three relationships give no extra information. However, the six remaining off-diagonal ones do! For example, the relationship for the (1,2) entry reads

$$cos(\alpha_{11})cos(\alpha_{21}) + cos(\alpha_{12})cos(\alpha_{22}) + cos(\alpha_{13})cos(\alpha_{23}) = 0$$

These 6 relationships relate all 9 parameters together (we can express one parameter in terms of the remaining). Thus, the number of "free parameters" is 3 (9 parameters - 6 constraints). Question answered! 

Even though the DCM is a fundamental attitude representation, it may not be the most appropriate one when you want to implement it in real applications. The fact that you carry 9 parameters, instead of only 3, and you need to enforce 6 non-linear constraints every time you update the orientation of an object makes the DCM inefficient. So let us look at alternative representations.


## Axis-angle representation

## Euler angles

## Quaternions





-----------------------------------------------------------------------------------------------------






