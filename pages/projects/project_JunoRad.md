---
layout: project_JunoRad
permalink: /project_JunoRad/
---

# Overview

The aim of this project is to characterize and understand the space environment of Jupiter’s polar regions, and specifically to understand the generation of Jupiter’s powerful aurora. In detail, we developed of a Jupiter high-energy particle radiation model from the energetic components of electrons and ions measured by JEDI and JADE instruments onboard the Juno spacecraft. To obtain the "true" high-energy particle flux, we removed an estimation of the background noisy particle flux using MULASSIS, a multi-layered Monte Carlo simulation tool for dose and particle fluence analysis associated with the use of radiation shields. This research was advised by Dr. Andersson and conducted at the Laboratory of Atmospheric and Space Physics (LASP) located in Boulder.

<figure style = "text-align: center">
  <img src="/assets/images/images_projects/main_junospacecraft_highres.jpg" width="70%">
  <figcaption style = "text-align: center"><small><strong>Figure 1:</strong> Juno spacecraft model and onboard instrumentation. Credit: NASA</small></figcaption>
</figure>

# Motivation

Extending beyond Jupiter’s moons, the Jovian magnetic field is the strongest in the solar system, except for the Sun’s. The field dominates an expansive region called the magnetosphere. The magnetic field accelerates electrically charged particles that stream through the magnetosphere. 
Most of these particles, which are ionized and swept up by the field, come from the volcanic gases spewing from Jupiter’s moon Io. Measuring the distribution of high-energy particles allows to understand the formation and composition of the Jovian magnetosphere, how the magnetic field accelerates these particles and estimate how fast Jupiter spins.

<figure style = "text-align: center">
  <img src="/assets/images/images_projects/Jupiter_magnetosphere_medres.jpg" width="70%">
  <figcaption style = "text-align: center"><small><strong>Figure 2:</strong> The magnetosphere of Jupiter. Credit: McComas, D. J., et al. 2017
</small></figcaption>
</figure>

# Method

In order to estimate the "true" particle flux detected by the anode of JEDI and JADE, we need to estimate the amount of  background noisy particle detections. JADE and JEDI employ electric fields to measure the energy and angular distribution of the particles in the Jovian magnetosphere. However, due to ionization and scattering through matter, the high-energy particles may traverse the different layers of materials that form JADE and JEDI and excite their anodes. This effect produces false detections, leading to inaccuracies when measuring the properties of the incoming "true" particles deflected by the electric fields.

We estimate the flux of background noise particles arriving at the anodes by modeling JADE and JEDI as a 1D multi-layered material strip given the shield map of each instrument. We simulate the flux of background noise using MULASSIS, a Monte-Carlo based software that simulates the amount of direct and scatered particles traversing each layer of material. Once background noise is removed from the measurements, we can estimate the "true" high-energy particle flux in the Jovian magnetosphere.  

<figure style = "text-align: center">
  <img src="/assets/images/images_projects/JADEEShieldingSlide.jpg" width="100%">
  <figcaption style = "text-align: center"><small><strong>Figure 3:</strong> Multi-layered 1D shield model to estimate the background noise particle flux impinging on the anode of JADE.
</small></figcaption>
</figure>

# More info

* [LASP - Magnetospheres of Outer Planets (MOP) reserach group](https://lasp.colorado.edu/home/mop/)

* [The Jovian Auroral Distributions Experiment (JADE) on the Juno Mission to Jupiter](https://link.springer.com/article/10.1007/s11214-013-9990-9)

* [The Jupiter Energetic Particle Detector Instrument (JEDI) Investigation for the Juno Mission](https://link.springer.com/article/10.1007/s11214-013-0025-3)
