---
layout: page
title: Bama-1 CubeSat Detumbling Model
time: Fall 2021
description: University of Alabama CubeSat Design Team
img: assets/img/bama1_pic.png
importance: 1
category: School
---

## Overview
BAMA-1 is a 3U CubeSat that was developed by the student design group UASpace in order to test drag sail technology for de-orbiting CubeSats from LEO. It was selected for the ELaNa 41 mission that launched on February 10, 2022. I was brought on in the summer of 2021 to create the attitude controls system and model of spacecraft dynamics and space environment.

<div class="row">
    <div class="col">
        <center>{% include figure.html path="assets/img/bama1_pic.png" title="BAMA1 illustration" class="img-fluid rounded z-depth-1" %}</center>
    </div>
</div>
<div class="caption">
    Illustration of BAMA-1 with a deployed drag sail (image credit: UA Space)
</div>


## Contributions

**B-dot Detumbling Algorithm**

BAMA-1 had four megnetometers that measured the strength and direction of Earth's magnetic field and three orthogonal magnetorquers that could apply torque to the CubeSat body. I used the B-dot algorithm with this all-magnetic sensing and actuation system to detumble the spacecraft from the high initial rotation rates it experiences following payload separation to rates suitable for mission objectives.

The picture below shows BAMA-1's three magnetorquers (two cylindrical torque-rods and one square air coil). By running a current through one of the wires, that magnetorquer creates a magnetic dipole. This interacts with the ambient magnetic field (in this case, the Earth's magnetic field) and induces a torque on the CubeSat body.

<div class="row">
    <div class="col">
        <center>{% include figure.html path="assets/img/bama1_bdot.png" title="Diagram of magnetorquer" class="img-fluid rounded z-depth-1" %}</center>
    </div>
</div>
<div class="caption">
    Diagram of the B-dot algorithm (Image credit: NanoAvionics)
</div>

In order to use these magnetorquers for detumbling, they must output torques on the CubeSat opposite to its rotational motion. The B-dot algorithm accomplishes this by calculating a magnetic dipole opposite to the rate of change of the magnetic field reading, which serves as a proxy for the rotation rate of the CubeSat. The torque created with this commanded dipole moment is in the opposite direction of the CubeSat's rotational motion, so it slows down.

I first simulated the B-dot controller and CubeSat dynamics in Simulink. The performance of one of these simulation runs is shown in the graph below. Once the gains were tuned to an appropriate value, I worked with the UASpace software lead to implement the controller in flight software.

<div class="row">
    <div class="col">
        <center>{% include figure.html path="assets/img/bama1_detumble.png" title="Detumble performance graph" class="img-fluid rounded z-depth-1" %}</center>
    </div>
</div>
<div class="caption">
    This graph shows the simulated performance of the B-dot algorithm for detumbling BAMA-1 with high initial rotation rates.
</div>

**Dynamics and Space Environment Modeling**

I modeled the dynamics of the CubeSat in six-degrees-of-freedom using two-body orbital motion and Euler's equation for rigid body rotational dynamics. The most important part of the space environment I modeled was the magnetic field model, so I used the high fidelity International Geomagnetic Reference Field (IGRF) model created by the International Association of Magnetism and Aeronomy.

After simulating the dynamics, controller, and Earth's magnetic field in Simulink in order to tune the B-dot controller gains, I wrote a Python script to simulate the motion of the spacecraft and the effects of the space environment. This was able to be used to test the CubeSat software and performing hardware-in-the-loop (HIL) testing.

**Post Script**

As a part of the ELaNa 41 mission, BAMA-1 was launched on February 10, 2022 on the Astra LV0008 rocket. There was a staging error during second stage separation, so BAMA-1 and the rest of the ELaNa41 payload were not able to achieve their intended orbits. UASpace has secured a spot for BAMA-2 on the next ELaNa program launch.

I presented this work with the BAMA-1 Software Lead at the AIAA Southeastern Regional Conference on April 4, 2022.