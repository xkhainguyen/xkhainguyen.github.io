---
layout: page
title: Breadth vs Depth
description: "CMU 16-813: Introduction to Robot Learning - Fall 23.<br> 🤖 Benchmarking Generalists and Specialists in Robot Learning"
img: assets/irl/irl_beam.gif
importance: 1
category: class
---
This is my project within the course [16-813: Introduction to Robot Learning](https://16-831.github.io/) at Carnegie Mellon University in Fall 2023 semester. 

Breadth vs Depth: Benchmarking Generalist and Specialist Policies in Robot Agility Learning \| Python, PyTorch, IssacGym, Unitree Go1 \|
 <!-- [[pdf](/assets/ards/F22_ARDS_Report.pdf)] [[slides](https://docs.google.com/presentation/d/1_4_3-siBjZcEE_0RPOMISLzRe4aqkGiOhhM8N28gGm0/edit?usp=sharing)] -->

---

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/irl/fig_abs.png" title="" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    We introduce a benchmark for learning robot agility on low-priced robots. Our study assesses both specialist and generalist policies, enabling robots to (a) traverse challenging terrain by (b) walking robustly, (c, d) climbing up and down high obstacles, (e) leaping over long gaps, and (f) crossing narrow beams only using one-side legs.
</div>

---

**Abstract**---The motivation for our project stems from the growing interest and importance of agile robots in various fields, including entertainment, search and rescue operations, and everyday tasks. As robots become more integrated into human environments, their ability to navigate complex and dynamic environments becomes crucial. Understanding whether a generalist or specialist approach is more effective in robot agility has direct implications for real-world applications. For instance, a generalist robot may be more versatile in handling different types of terrain commonly found in various environments, while a specialist robot may excel in specific scenarios. Knowing which approach is more effective can guide the development of robots for specific tasks or environments.
By addressing these motivations, our project can contribute valuable insights to the field of robotics and help advance athletic intelligence that enables navigating and interacting with complex environments effectively.

---

<span style="color:blue"> Stay tuned for more updates!</span>

<iframe height="433" src="https://www.youtube.com/embed/_TqcasN4f5c?si=T5FXf7TeYjyc5ist" title="YouTube video player" frameborder="0" style="border: 0px solid #bbb; border-radius: 10px; width: 100%;" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen=""></iframe>
<div class="caption">
    Go1 robot is able to traverse challenging terrain: steps, gaps, narrow beams
</div>

## Approaches

Our research lays the foundation for a comprehensive benchmark in evaluating diverse learning-based approaches for robot agility. We introduce three distinct baselines: i) specialist policies that acquire individual skills through on-policy reinforcement learning; ii) a hierarchical structure featuring a policy/skill selector that learns to choose the appropriate behavior among these specialists; and iii) a true generalist policy that simultaneously learns to handle all tasks. Additionally, we explore the policy/skill selector's performance under two training paradigms: on-policy reinforcement learning and imitation learning based on an oracle policy.

We seek to answer these questions:

- Does a specialist generalize to new terrains, e.g., can the robot traverse gap terrains with learned climbing skills?
- Does the generalist benefit from learning multiple skills, e.g., can climbing and leaping skills help each other while learned simultaneously?
- Does the hierachical structure outperform the generalist, e.g., should we instead leverage modular approaches -- a high-level task/skill selector and low-level skills?

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/irl/policy_selector.png" title="" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The hierachical structure features a policy/skill selector that learns to choose the appropriate behavior among these specialists. This can be trained via on-policy reinforcement learning or imitation learning based on an oracle policy.
</div>
