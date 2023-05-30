---
layout: page
title: advanced and intelligent control
description: nonlinear systems; adaptive, robust and optimal control; reinforcement learning
img: assets/img/publication_preview/khai2021thesis2.png
importance: 2
category: lab
---

This is my previous set of projects at the Advanced Control and Robotics at Hanoi University of Science and Technology. Several papers and thesis are listed in [publications](/../publications){:target="_blank"} page. Some key points:

- Explored motion/force robust controller for multiple mobile manipulators to accomplish co-operative tasks.
- Integrated control theory to boost stability and robustness of reinforcement learning algorithms (actor-critic) by 66%.
- Devised hierarchical formation control for multi-agent systems; scaled up and simulated with MATLAB/Simulink.

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.html path="assets/img/publication_preview/khai2021thesis2.png" title="disturbance observer" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/publication_preview/khai2022formation.gif" title="formation control" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    On the left, tracking performance is improved by RL controller with disturbance observer. <br>
    Right, multi-agent formation control with RL.
</div>

My Bachelor thesis proposed the combination of RL/ADP-based design and nonlinear methods to develop robust approximately optimal control for continuous nonlinear systems with uncertainties and disturbances. 

- One contribution is the introduction of time-varying robust integral of the sign of the error (RISE) into
RL-based control of second-order nonlinear systems. Matlab simulation results on a 2-DOF robot arm demonstrate the improved performance of the
time-varying RISE-based RL scheme in comparison with the original RISE-based RL controller.
- Another innovation is the disturbance observer-based RL control approach which not only learns the optimal policy but also learns the unknown disturbances. To verify the advantages of the proposed control structure, a comparison with the original RL-based method is made, implementing a surface vessel system simulation.