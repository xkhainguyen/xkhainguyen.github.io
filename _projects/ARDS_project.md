---
layout: page
title: Stability SOS
description: "CMU 16-715: Advanced Robot Dynamics & Simulation - Fall 22.<br>🆘 Stability Verification Using Sum-of-Squares Programming"
img: assets/ards/vanderpol_roa_cropped.png
importance: 1
category: class
---
This is my project within the course [16-715: Advanced Robot Dynamics & Simulation](https://github.com/dynamics-simulation-16-715) at Carnegie Mellon University in Fall 2022 semester. Some key points:

Stability Verification via SOS \| Python, Drake, Mosek \| [[pdf](/assets/ards/F22_ARDS_Report.pdf)] [[slides](https://docs.google.com/presentation/d/1_4_3-siBjZcEE_0RPOMISLzRe4aqkGiOhhM8N28gGm0/edit?usp=sharing)]

- Verified the Lyapunov stability of dynamical systems by formulating and solving sum-of-squares programs with Mosek, compared with Drake.
- Implemented and compared three different approaches; sample-based method gained tighter solution 30 times faster than standard one.

---

**Abstract**---We explore sampling-based sum-of-squares (SOS) programming as a technique to verify the stability of nonlinear systems. We provide a review of Lyapunov analysis, traditional SOS stability verification, and sampling-based SOS verification, then apply these methods to two nonlinear systems. We demonstrate that sampling-based SOS verification offers significant advantages over the traditional formulation in terms of problem size and the amount of time required to obtain a solution. The code for this project is available at [link](https://github.com/EpicDuckPotato/final_project_16715.git).

**Results**

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.html path="assets/ards/vanderpol_roa.png" title="vanderpol roa" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Van der Pol region of attraction approximations.
</div>