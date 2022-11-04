---
layout: page
title: GEO Satellite Formation Flying
time: Summer 2022
description: Astranis Space Technologies
img: assets/img/astranis_geo_slot.png
importance: 1
category: Work
---

## Overview
In late 2022, Astranis will launch a small satellite to geostationary orbit (GEO) that will provide broadband internet to rural Alaska. While space in GEO is typically assigned in slots for a single satellite, Astranis plans to send four satellties to share the same slot for their next launch. In order to do this safely, the GNC team and I needed to develop strategies to maintain passive separation of the satellites over one orbit while keeping all the satellites in their designated area.

<div class="row">
    <div class="col">
        <center>{% include figure.html path="assets/img/astranis_geo_slot.png" title="GEO Slot" class="img-fluid rounded z-depth-1" %}</center>
    </div>
</div>
<div class="caption">
    The box represents the space in geostationary orbit allocated to Astranis. All four satellites must maintain separation from each other without violating these bounds.
</div>

## Contributions

**Passive Separation Analysis**

By carefully selecting inclination and eccentricity vectors to provide radial and normal seperation between orbits, the satellite's paths are guaranteed not to interesect. I created a tool that defined relative inclination and eccentricity vectors for the four satellites according to the inclination and longitude limits of the GEO slot. It also determined the initial state of all the satellites in classical orbital elements based on these relative vectors and a reference state. This allowed for analysis of the distance between satellites and simulation of the satellite motion, and it will serve as a key tool to design and validate GNC guidance algorithms.


<div class="row">
    <div class="col">
        <center>{% include figure.html path="assets/img/ecc_vecs.png" title="Eccentricity vector effects" class="img-fluid rounded z-depth-1" %}</center>
    </div>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <center>{% include figure.html path="assets/img/inc_vecs.png" title="Inlcination vector effects" class="img-fluid rounded z-depth-1" %}</center>
    </div>
</div>
<div class="caption">
    Inclination and eccentricity vectors create separation between orbits in the radial and tangential directions, respectively. By making them parallel, the intersection points associated with one of the vectors coincides with the point of maximum separation due to the other vector, so the orbits are completely separated.
</div>


**Formation Stationkeeping Guidance**

The satellites will be able to maintain relative separation indefinitely by starting in the right orbits, but they will drift out of the designated GEO slot due to perturbations unless the orbits are corrected periodically. Stationkeeping maneuvers serve this purpose. 

The existing stationkeeping guidance was only able to plan maneuvers for a single satellite in a GEO slot, so I updated the guidance to handle multiple satellites within the same slot. This maintained existing functionality while expanding the capability of the simulation framework to examine stationkeeping performance of different satellites in the multi-satellite formation.

**Monoprop Thruster Angle Optimization**

These two contributions supported the simulation of the satellites in formation. My final project was to use this framework to optimize the angles of the monopropellant thrusters for the satellites based on fuel usage over the course of a year. 

To do this, I ran a grid search over possible thruster angles. In each grid point (which represents one set of thruster angles), I ran a small Monte Carlo simulation to assess the average fuel usage across varying parameters of the satellites, such as initial position and remaining propellant mass. This process was iterated around the angle sets with the lowest fuel usage to identify the thruster angle set that will result in the most efficient stationkeeping.
