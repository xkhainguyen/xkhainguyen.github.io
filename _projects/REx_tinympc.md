---
layout: page
title: TinyMPC
description: fast and low-memory footprint MPC solver for resource-constrained embedded systems
img: assets/rex_lab/tinympc_cropped.png
importance: 1
category: lab
---

I'm co-leading the development of TinyMPC, a specialized control solver for embedded systems. Our main goals are to make it faster and use less memory. In benchmarks, TinyMPC outperforms OSQP in both speed and memory usage. We've implemented TinyMPC on the Crazyflie, a 27 g nano-quadrotor, enabling it to move quickly and avoid obstacles effectively.

But that's not all! TinyMPC is open-source and well-documented, ensuring everyone can access real-time optimal control easily.

For more details, visit <https://tinympc.org>.

Side-story: I experimented with various methods and started with augmented Lagrangian (AL) with linear-quadratic regulator (LQR) ([repo](https://github.com/RoboticExplorationLab/TinyMPC-AL)). The report for Optimal Control and RL class is [here](/assets/pdf/OCRL_Final_Report.pdf). However, I found these methods to be too slow. We switched to the alternating method of multipliers (ADMM) and are seeing promising results on hardware.
