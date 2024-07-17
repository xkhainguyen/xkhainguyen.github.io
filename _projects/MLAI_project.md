---
layout: page
title: Learned Legibility
description: "CMU 24-782: MLAI - Spring 24.<br> 🦾 Viewpoint-Conditioned Legible Motion Planning with Imitation and Reinforcement Learning"
img: assets/img/legibility_thumb.gif
importance: 1
category: class
---
This is my project within the course 24-782: Machine Learning and Artificial Intelligence at Carnegie Mellon University in Spring 2024 semester.

**Viewpoint-Conditioned Legible Motion Planning with Imitation and Reinforcement Learning** \| Python, Gym, RL Baselines3 Zoo, MuJoCo, xArm6 \|
 [[pdf](/assets/pdf/Legibility_Report.pdf)] [[poster](/assets/pdf/Legibility_Poster.pdf)]

We proudly presented this work -- A Robot Learning System for Viewpoint-aware Legible Motion Planning --  at the Robotics: Science and Systems (RSS 2024) Workshop Learning for Assistive Robotics. [[site](https://sites.google.com/view/rss2024-assistive-robotics/home-page)] [[pdf](/assets/pdf/RSS24W-Legibility.pdf)] [[poster](/assets/pdf/RSS24W-Legibility-poster.pdf)]

---

**Abstract**---Legibility is a crucial concept in terms of efficiency and trust in assistive robotics and human-robot collaboration, where the robot communicates its objectives through its actions in an understandable and predictable manner. Traditional motion planning techniques encounter various issues, including high computational latency, ambiguous objectives, and intensive tuning efforts. To overcome these challenges, we propose a universal planning architecture for learned legible behaviors using reinforcement learning and imitation learning. Furthermore, we introduce a novel planning model that considers human’s viewpoint to generate adaptive motions that more effectively express intents. The effectiveness of our frameworks is validated through goal-reaching manipulation tasks conducted using the xArm6 robot in both simulated environments and real-world settings. Human-based evaluations indicate that our trained agent outperforms expert demonstrations by 15%. Our implementation
can be accessed at [https://github.com/BernieChiu557/xarm6-RL](https://github.com/BernieChiu557/xarm6-RL).