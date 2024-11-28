---
layout: page
title: F1TENTH 
description: 🏁 1/10th-scale autonomous racing
img: assets/misc/f110_cropped.png
importance: 1
category: misc
---

I was a core member of CMU's F1TENTH team. Based on the [F1TENTH platform](https://f1tenth.org/) (you can even spot me on the website), we built a 1:10 scaled autonomous race car and developed autonomy software including SLAM, state estimation, raceline optimization, and tracking control. It is able to perform head-to-head racing and reach maximum velocity of 20 km/h. I participated in the [competition](https://cps2023-race.f1tenth.org/) in San Antonio within the Cyber-Physical Systems and Internet-of-Things Week in May 2023 and the team advanced to semi-final.

During my involvement, I worked on integrated planning and control from simulation to hardware. Things I used for the project

- SLAM: ROS 2 slam_toolbox
- State estimation: [particle filter](https://github.com/mit-racecar/particle_filter)
- Raceline optimization: [TUM software](https://github.com/TUMFTM/global_racetrajectory_optimization)
- Control: gap-following, wall-following, PID, pure-pursuit, MPC.

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/misc/f110.gif" title="ball and beam" class="img-fluid rounded z-depth-1" %}
      <div class="caption">
      Autonomous driving during the race.
      </div>
    </div>
    <div class="col-sm-6 mt-3 align-self-center">
        {% include figure.liquid loading="eager" path="assets/misc/f110_map.jpg" title="formation control" class="img-fluid rounded z-depth-1" %}
      <div class="caption">
      Race map.
      </div>
    </div>
</div>

Note: we ended up using simple methods for the race.
