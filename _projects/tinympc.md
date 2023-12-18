---
layout: page
title: TinyMPC
description: fast and low-memory footprint MPC solver for resource-constrained embedded systems
img: assets/rex_lab/tinympc_logo_cropped.png
importance: 1
category: lab
---

I'm co-leading the development of TinyMPC, a specialized control solver for embedded systems. Our main goals are to make it faster and use less memory. In benchmarks, TinyMPC outperforms OSQP in both speed and memory usage on the *Teensy microcontroller*. We've integrated TinyMPC on the Crazyflie, a 27 g nano-quadrotor, enabling it to maneuver and avoid obstacles effectively.

But that's not all! TinyMPC is **open-source** and well-documented, ensuring everyone can access real-time optimal control easily.

For more details, visit <https://tinympc.org>.

Side-story:

- We started from our Optimal Control & Reinforcement Learning class [project](/projects/OCRL_project). I experimented with various methods and started with augmented Lagrangian (AL) with linear-quadratic regulator (LQR), which can also handle nonlinear dynamics [[repo]](https://github.com/RoboticExplorationLab/TinyMPC-AL). However, we found these methods to be too slow. We switched to the alternating method of multipliers (ADMM) and are seeing promising results on hardware.

- I did a perching demo with TinyMPC here just for fun. It crashed since I didn't use any sticking mechanism.

<iframe height="433" src="https://www.youtube.com/embed/KoU2wr9nAFI?si=xOhNq-maZIsaCQWE" title="YouTube video player" frameborder="0" style="border: 0px solid #bbb; border-radius: 10px; width: 100%;" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen=""></iframe>
