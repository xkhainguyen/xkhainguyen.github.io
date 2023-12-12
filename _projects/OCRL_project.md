---
layout: page
title: TinyMPC
description: "CMU 16-715: Optimal Control & Reinforcement Learning - Spring 23.<br> 🎮 TinyMPC: A Model Predictive Control for Embedded Applications"
img: assets/rex_lab/tinympc_cropped.png
# redirect: /projects/REx_tinympc/
importance: 1
category: class
---

This is my project within the course [16-715: Optimal Control & Reinforcement Learning](https://github.com/Optimal-Control-16-745/) at Carnegie Mellon University in Spring 2023 semester. Some key points:

TinyMPC: A Model Predictive Control for Embedded Applications \| C/C++, Julia, Python, Crazyflie, STM32, Teensy \| [[pdf]](/assets/pdf/OCRL_Final_Report.pdf) [[slides]](https://docs.google.com/presentation/d/1cFMTpDRfxqL3kF0Zi5DV3jDhsEP8uIU8RSy6qDEq0X8/edit?usp=sharing)

- Led a team to develop a novel efficient convex model-predictive control algorithm targeting embedded systems.
- Introduced a new full-state quaternion-based LQR/LQI controller onto Crazyflie (C/C++ on STM32); accomplished robust hovering performance.
- Evaluated the augmented Lagrangian-based MPC solver on Teensy Arduino and STM32F4.

---

**Abstract**---We introduce a novel model predictive control
(MPC) framework designed for running on low-resource hardware. Our approach utilizes an Augmented Lagrangian-iLQR
optimization method to handle trajectory optimization and
constraint management. The framework is optimized to run on
several microcontrollers, including the Teensy 4.1, STM32F401,
and the Crazyflie 2.1 drone, which uses an STM32F405
processor. We detail the algorithm implementation, hardware
optimization techniques, and provide a comparison of the
framework’s runtime performance with other state-of-the-art
solvers. Additionally, we present the results of testing the
framework on the Crazyflie 2.1 drone, which shows that it
can solve the full-state quadrotor problem with a minimum
frequency of 16Hz, while a complementary LQR is implemented
to stabilize the drone at 50Hz.

---

For more details, please check our report.

## Introduction

In recent years, significant strides have been made in
the field of robotics, particularly in deep learning (DL)
and reinforcement learning (RL), resulting in a range of
improved capabilities and applications. However,
these advanced techniques often demand significant computing resources, which can pose challenges for many robotic
applications. This stands in contrast to a significant portion
of robotics that utilizes embedded systems with severely
limited computing resources. These systems include palmsized toy robots like the Crazyflie quadrotor and the
Petoi Bittle quadruped, as well as mission-critical robots
like NASA’s Mars Perseverance rove. The Crazyflie
and Bittle employ affordable and accessible commercial
microcontrollers, such as families of STM32 and Teensy,
respectively. Meanwhile, the Perseverance rover relies on
RAD750, a radiation-hardened version of the PowerPC 750
processor from the previous century. Clearly, the need for
resource-constrained robotic applications is widespread. Operating within a tight computational budget, these embedded
systems require innovative approaches to enable the efficacy
of advanced techniques.

Our contributions to the field of optimal control are
three-fold. Firstly, we have developed a highly efficient and
extensible open-source optimal control solver in C. Secondly,
we have created a user-friendly MPC interface that simplifies
the setup and compilation of our solver on various hardware
platforms. Finally, we have provided benchmark results to demonstrate the efficacy of our approach and a hardware
demonstration to showcase its practicality.

## Design

### Constrained Optimal Control Problem

Up to this point, we have not considered any constraints on
the state x or input u. Real-world systems have many types
of physical or desired limitations. Some popular constraints
are box constraints on the state and input at each time step
(to ensure that the solution is realizable on hardware and to
encourage smoothness in the solution), equality constraints
on the goal state (to ensure that that a desired final position is
reached), and second-order cone constraints to, for example,
enforce thrust limits.

To handle constraints, we use the augmented Lagrangian
method (ALM) which enforces constraints into the cost
function. Generally, our tracking problem is convex, and
a global solution can be found with only one constrained
backward pass. However, multiple iterations are needed to
satisfy dual feasibility.
Below is the pseudo-code of our AL-TVLQR algorithm.

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.html path="assets/acsi/plan_flip.png" title="Title" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Generalized flipping speed reference in previous work
</div>

The flipping planner outputs a trajectory for the quadrotor
to follow. This is divided into five stages as follows:

- Ascent phase: Here the quadrotor is boosted to obtain
moments and inertia before executing the flip.
- Increasing angular velocity phase: In this stage, the roll
rate slowly increases from 0 to ωmax.
- Max angular velocity phase: At this stage the ωmax is
commanded.
- Decreasing angular velocity phase: In this stage, the roll
rate decreases from ωmax to 0.
- Stabilizing phase: This phase is activated after a complete
flip. The quadrotor is stabilized and enters normal flight
mode

### Flipping Controller

Following the previous work, a [PD-like controller](https://ctms.engin.umich.edu/CTMS/index.php?example=Introduction&section=ControlPID) is designed for tracking the angular velocity from the planner.

$$
u(t) = k_p e(t) + k_d \dot{e}(t)
$$

The PD controller can be tuned to obtain a desired behavior from the controller by varying the $$k_p$$ and $$k_d$$ terms. This controller provides the control efforts in the form of three torques, and a thrust is set as the drone’s weight to maintain a constant height and not to saturate the actuators.

### Stabilizing Controller

An [LQR controller](http://underactuated.mit.edu/lqr.html) is designed to re-stabilize the drone after a complete flip. It is noteworthy that we require a robust controller because initial errors for this controller can be significant. LQR controller is a full-state feedback controller and is designed using the linearized mathematical model of the quadrotor. An optimization problem is solved to obtain the gains of the LQR controller. The LQR controller is tuned by varying the $$Q$$ and $$R$$ matrices to get the desired performance from the controller.

## Results

There are several testing cases for flipping maneuvers depending on open-loop vs. closed-loop planner, not tuned vs.
tuned attitude rate PID, and PID vs. LQR stabilizer. Single flip is tested first with detailed analysis before moving to the more challenging cases. Please see our report for more details.

<div class="row justify-content-sm-center">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.html path="assets/acsi/flip_steps.png" title="Title" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Snapshots of our flipping maneuver from the demo video
</div>

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-1 mt-md-0">
        <iframe height="600" src="https://www.youtube.com/embed/81XYgRthhc0" title="YouTube video player" frameborder="0" style="border: 0px solid #bbb; border-radius: 10px; width: 100%;" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen=""></iframe>
    </div>
    <div class="col-sm-6 mt-1 mt-md-0">
        <iframe height="600" src="https://www.youtube.com/embed/y1OanjJ8mtQ" title="YouTube video player" frameborder="0" style="border: 0px solid #bbb; border-radius: 10px; width: 100%;" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen=""></iframe>
    </div>
</div>
<div class="caption">
    Left: LQR hovering <br> Right: Autonomous flip
</div>

## Conclusions

This work has provided a complete flipping maneuver
pipeline which is very challenging for a micro quadrotor’s
acrobatic application. Our approach divides the process into
three steps: ascent, flipping and re-stabilization. Following
that, we developed a flipping planner, a flipping controller,
and a stabilizing controller. An open-loop flipping planner
will generate a three-stage attitude rate reference based on
time, compared to the generalized flipping angle feedback of
a closed-loop one. This planner must consider the limited
sensing and actuating capacity of the quadrotor. To track
that reference, we use a flipping controller, which has a PD-like architecture, then switch to a regular controller after
completing a flip. For that re-stabilization phase, both cascaded
PID and LQR controllers are considered. These modules are
implemented via Python API as well as directly Crazyflie
firmware. Finally, this paper has detailed experimental testing
and demonstrated successful flip maneuvers. However, the
majority of the tests witness failures due to many different
factors, including communication delay, open-loop drawbacks,
and not-robust-enough LQR controllers.
Many modifications to the current pipeline can be made to
improve the performance in the future. Firstly, the closed-loop
planner, which needs more integration tests, has provided the
stabilizing controller with good initial conditions. Secondly,
all modules should be directly implemented in the on-board
microprocessor, which will significantly help with the delay problem. Last but not least, more accurate state measurements
and different architectures can boost the LQR stabilizer’s
robustness and overall performance.