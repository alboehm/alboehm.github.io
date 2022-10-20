---
layout: page
title: Solar Sail Momentum Management Model
description: Summer 2021 Internship, NASA MSFC - Control Systems Design and Analysis Team
img: assets/img/rcds.png
importance: 4
category: work
---

## Overview
During the summer of 2021, I worked in the Control Systems Design and Analysis group at NASA Marshall Space Flight Center. I served on the Attitude Determination and Control Systems team and supported the creation of the plant and flight software models for Solar Cruiser, a solar sail with planned for launch in 2025. Solar Cruiser is a technology demonstration mission, so one of its mission goals is to develop and test the technology for using Reflectivity Control Devices (RCDs) for momentum management. 

RCDs are composite materials with a layer of liquid crystal that turns translucent when a voltage is applied. When light strikes an activated RCD, it bounces off the aluminum backing and creates specular reflection. This generates a stronger force vector than when the more diffuse reflection that occurs when the RCDs do not have voltage applied to them. This is illustrated in the diagram below. By setting the RCDs at an angle to the sail and aligning them along each of the four booms, they can be used to trim roll momentum (for solar sails, roll is the rotation of the sail in-plane). Rather than acting directly on the sail's rotational momentum, the RCDs will be used to desaturate the reaction wheels when their rotational speed gets too high.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/rcds.png" title="rcds" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Visual difference in RCD reflectivity (image credit: JAXA)
</div>

## Contributions
My main project was to develop a model of both the plant and flight software for the RCDs on the sail, and then integrate it into the existing overall sail simulation. I was unfamiliar with the process of creating controls systems, so I researched theory and applications (big thanks to Steve Brunton and Brian Douglas!). Then, I built a simple 1-D model of the RCDs controlling for the momentum of the sail in the z-direction. The RCDs only have two options for commands, ON (voltage applied) or OFF (voltage not applied), so the controller design was quite simple. Depending on the error, the controller would send one of three commands: 1, telling one set of RCDs to turn ON while the other set stays OFF in order to apply a positive moment to the sail; -1, telling the RCDs sets the opposite command in order to apply a negative moment to the sail; and 0, telling both RCD sets to turn off. This command is then sent to the plant model, where the moment applied to the sail by the RCDs is calculated.

From this 1-D model, I added complexity until I had a standalone model that described behavior in 3-DOF and incorporated the effects of a changing center of mass. Then, I integrated the model into the Solar Cruiser simulation. The graphs below show the performance of the RCD system in this simulation. When the reaction wheel momentum (in the bottom chart) passes the activation value, the RCDs trigger to apply a moment opposite to the momentum to drive it back towards 0. The controller successfully manages the momentum of the reaction wheels, even after the slew maneuver occurs, in which the sail drastically changes attitude.

This project confirmed my interest in pursuing graduate school for GN&C with a focus on controls.


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/rcd_performance.png" title="rcd_graphs" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    These graphs show the performance of the RCD model in the Solar Cruiser simulation. When the reaction wheel momentum (bottom chart) leaves the activation band, the RCDs are triggered to apply a moment to the sail, driving the momentum back towards zero.
</div>

<!---center rcd pic--->