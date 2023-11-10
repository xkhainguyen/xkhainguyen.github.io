---
layout: page
title: Legged MPC
description: "24-785: Engineering Optimization - Fall 22.<br> 🦿 Quadruped Locomotion Through Nonlinear MPC"
img: assets/engopt/leg_cropped.gif
importance: 1
category: class
---
This is my group project within the course [24-785: Engineering Optimization](/assets/engopt/Syllabus-1.pdf) at Carnegie Mellon University in Fall 2022 semester. Some key points:

Nonlinear MPC on Quadruped Robot \| C/C++, OCS2 \| [[pdf](/assets/engopt/24_785_Project.pdf)] [[slides](https://docs.google.com/presentation/d/1JM6_66rsDxseqxBFta2RHyDQaOb0_o3t/edit?usp=sharing&ouid=112223428720998799657&rtpof=true&sd=true)]

- Collaborated to establish nonlinear MPC formulation of quadruped robots, considering tracking errors, centroidal dynamics, joint limits and friction constraint; achieved dynamic walking gait.
- Analyzed MPC implementation on ANYmal from an optimization perspective including SQP formulation and sensitivity analysis.

---

**Abstract**---The control of dynamic-legged locomotion poses a significant challenge due to the under-actuation of the system and the uncertainty inherent in the external environment. In this project, we implemented a control framework based on nonlinear model predictive control (NMPC) to enable the dynamic walking of a quadruped robot. The final deliverable is a controller that can control the ANYmal robot in simulation to walk steadily on flat ground with a trotting gait using the OCS2 toolbox and the sequential quadratic programming (SQP) solver. To achieve this, we solved the optimization problem using real-time iteration, filter-based line search, and constraint projection. Our results indicate that the solver is sensitive to the initial guess of states and is able to find a local minimum that is very close to the global minimum, as validated based on physics.

**Results**

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.html path="assets/engopt/leg.gif" title="legged mpc" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Quaduped walking gait.
</div>