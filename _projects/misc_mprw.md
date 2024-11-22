---
layout: page
title: MIT-PITT-RW
description: 🏁 full-scale autonomous racing
img: assets/misc/mprw_cropped.jpeg
importance: 1
category: misc
---

I was a member of [MIT-PITT-RW](https://www.mitpittrw.com/), "a joint team between University of Pittsburgh, Rochester Institute of Technology (RIT), University of Waterloo, and Massachusetts Institute of Technology (MIT) Driverless team. Its mission is to be the center for applying autonomous vehicle technology across each of our partner schools and to create and implement cutting edge technology in the AV field."

During my short involvement, I worked on model predictive path integral ([MPPI](https://sites.gatech.edu/acds/mppi/)) method (beneficial from GPU computing), where I verified its functionalities (optimal trajectory planning, obstacle avoidance, etc) and directly discussed further improvements with the team's chief engineer. In the near future, I want to benchmark MPPI vs MPC and investigate a more sample-efficient technique.

Unfortunately, I am taking a break from the team.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/misc/mppi.gif" title="wireless charging" class="img-fluid rounded z-depth-1" %}
      <div class="caption">
          Overtaking demo with MPPI: reference (green), seed (yellow), rollouts (red), optimal plan (blue). The car swerves to the right to pass the leading opponent. (Refresh tab to see the gif again)
      </div>
    </div>
</div>

