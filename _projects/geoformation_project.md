---
layout: page
title: GEO Satellite Formation Flying
description: Summer 2022 Internship - Astranis Space Technologies
img: assets/img/astranis_geo_slots.png
importance: 4
category: work
---

## Overview
In late 2022, Astranis will launch a small satellite to geostationary orbit (GEO) that will provide broadband internet to rural Alaska. Although space in GEO in limited, Astranis has big plans. The next generation of Astranis internet satellites will be composed of up to four individual satellites that share a single GEO slot. In order to do this safely, we needed to develop strategies to maintain passive separation of the satellites over one orbit while keeping all the satellites in their designated area.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/astranis_geo_slots.png" title="GEO Slot" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The box represents the space in geostationary orbit allocated to Astranis. All four satellites must maintain separation from each other without violating these bounds.
</div>

## Contributions

**Passive Separation Analysis**
By carefully selecting each satellite's orbit, we can ensure the satellites will not collide over short periods of time without the use of any fuel. Parallel relative inclination and eccentricity vectors provide radial and normal separation between the satellites, so they are guaranteed separation over the course of the entire orbit.

<div class="row justify-content-sm-center">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/ecc_vecs.png" title="Eccentricity vector effects" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/11.jpg" title="Inlcination vector effects" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Inclination and eccentricity vectors create separation between orbits in the radial and tangential directions, respectively, but used individually, there are still intersection points. By making them parallel, the intersection points associated with one of the vectors coincides with the point of maximum separation due to the other vector, so the orbits are completely separated.
</div>

I created a tool that defined relative inclination and eccentricity vectors for four satellites according to the inclination and longitude limits of the GEO slot. It also determined the initial state of all the satellites in classical orbital elements based on these relative vectors and a reference state (typically, the center of the GEO slot). This allowed for analysis of the satellite separation distances and simulation of the satellite motion.

**Formation Stationkeeping Guidance**
While the satellites may be able to maintain separation indefinitely by starting with the right set of orbital elements, they will drift out of the GEO slot without correction due to inclination and eccentricity vector drift. This requires stationkeeping maneuvers, but the guidance that was created for a single satellite needed an overhaul to work with multiple satellites. In the existing guidance, the satellite performed a stationkeeping maneuver when the magnitude of the longitude, eccentricity, or inclination started to violate its GEO slot bounds. I updated the guidance to interpret inclination and eccentricity as vectors rather than magnitudes and to redefine its understanding of the satellite slot based on parameters set in a simulation config file. This maintained existing functionality while expanding the capability of the simulation framework to examine stationkeeping performance of different satellites in the multi-satellite formation.

These two contributions, the tool that initializes the states of each satellite and the updated guidance, supported the simulation of the satellites in formation. I also used this framework to optimize the angles of the monopropellant thrusters for the satellites based on the monopropellant usage over the course of a year.
