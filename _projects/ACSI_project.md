---
layout: page
title: autonomous flip
description: "24-774: Advanced Control Systems Integration - Fall 22.<br> Drone Acrobatics: Autonomous Flip"
img: assets/acsi/flip.gif
importance: 1
category: class
---
This is my group project within the course [24-774: Advanced Control Systems Integration](/assets/acsi/24-774%20Syllabus%20Fall%202022.pdf) at Carnegie Mellon University in Fall 2022 semester. Some key points:

Drone Acrobatics: Autonomous Flip | C/C++, MATLAB/Simulink, Python, Crazyflie	
- Led a team to derive an autonomous multi-flip pipeline for nano-quadrotors and successfully verified it in simulation.
- Introduced a new LQR controller onto Crazyflie (C/C++ on STM32); accomplished robust hovering performance.
- Implemented flip planner, flip controller and re-stabilizing controller; delivered single-flip maneuver with Crazyflie.

**Abstract** -- Drones are popular due to their ability to take off and land vertically, high maneuverability, and hovering capability. However, they are highly unstable and susceptible to external disturbances. In this project, we examine flip maneuver which exploits the quadrotor's agility while maintaining stability simultaneously. The flipping pipeline consists of three main modules: trajectory planner, tracking controller and stabilizing controller. A smooth three-stage flipping rate profile is generated in account for the limited sensing and actuating capabilities of the micro quadrotor. A PD controller is used for executing the rapid trajectory for the flip, then switched to a cascaded PID to re-stabilize the quadrotor during normal flight. Beside, a full-state feedback LQR controller is designed to test with the stabilization phase. These modules provide the drone with an ability to perform autonomous flip. Simulation and experimental tests on a Crazyflie quadrotor are successful. However, hardware performance is not consistent and in need of further works.

**Results**
<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        <iframe width="420" height="315"
            src="https://www.youtube.com/embed/81XYgRthhc0">
        </iframe>
        <iframe width="420" height="315"
            src="https://www.youtube.com/embed/y1OanjJ8mtQ">
        </iframe>
    </div>
</div>
