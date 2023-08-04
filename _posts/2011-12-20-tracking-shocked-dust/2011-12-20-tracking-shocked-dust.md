---
title: "Tracking shocked dust"
date: "2011-12-20"
categories: 
  - "work"
---

Our group's latest paper has been ~~accepted for publication~~ _published_ in Physics of Plasmas:

"Tracking shocked dust: state estimation for a complex plasma during a shock wave" Neil P. Oxtoby, Jason F. Ralph, Céline Durniak and Dmitry Samsonov.

Read the abstract and download from [Physics of Plasmas DOI 10.1063/1.3678201](https://doi.org/10.1063/1.3678201) or [arXiv:1112.5316](http://arxiv.org/abs/1112.5316).

Overview: The motion of "dust" particles in a complex plasma are obtained by computer-processing frames of a high-speed video. This gives us particle positions as a function of time. An individual particle's velocity is usually obtained from consecutive positions — a technique known as particle tracking velocimetry (PTV). This yields an estimate of _average_ velocity between frames with precision limited by the precision of the particle's positions. In particular, pixel locking will propagate into velocity estimated using PTV. We include a Bayesian inference step in the tracking procedure - using an extended Kalman filter to predict the particle position, velocity and acceleration. The prediction is based on a priori knowledge of the dust dynamics. We show that Prediction + Measurement (in a weighted sum) = significantly higher precision than PTV. We also go further to use an interacting multiple model (IMM) filter that handles the shock wave excitation nicely - see the paper for details (quite technical).

The bottom line for physics: Target tracking (state estimation) can significantly improve the precision of velocity estimates for the dust. This is of major importance for calculating condensed-matter-like quantities such as pressure/stress, kinetic temperature, and dynamic viscosity — to name a few. We calculated a pressure-volume diagram from our results, showing excellent qualitative agreement between experiment and simulation.
