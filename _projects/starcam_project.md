---
layout: page
title: Startracker Thermal Boresight Testing
time: Summer 2023
description: Planet
img: assets/img/astranis_geo_slot.png
importance: 1
category: Work
---

# TODO:
* update image for projects page
* edit overview
* write contributions

## Overview

Planet is a satellite Earth observation company that provides high-frequecy goespatial data. In order for satellites in LEO to take high-quality images of the Earth, the satellites must have fine pointing knowledge and control. My project focused on characterizing the uncertainty of the highest precision attitude sensor, the startrackers, sepcifically relating to their performance under thermal loads.

A startracker is a sensor that estimates spacecraft attitude in inertial space. It is composed of a camera and a small computer. It works by taking an image of the starfield, finding the locations of the stars in the image, and comparing these to known locations of stars in a catalog stored on its computer. Any drift of the stars in the camera sensor is interpreted as a change in the spacecraft attitude. Typical startracker accuracy is on the level of arcseconds (1/3600 of a degree).

Ideally, a startracker is athermal, and the attitude estimate is uncorrelated with the startracker temperature. However, heat causes materials to expand, which is seen by the startracker camera sensor as a shift in the starfield. Thus, thermal load on the startracker can introduce error into the spacecraft attitude estimate, and this error needs to be characterized in order to understand the uncertainty of the startracker attitude estimate. Specifically, my goal was to identify the startracker components that were deforming the most due to temperature, and to quantify the error in arcseconds per unit temperature.

ADD PHOTO OF SHIFTING STARFIELD


## Contributions

To test the thermal affects on the startracker attitude estimate, I setup a testbed with a light source and startracker. Diffuse light would shine through very small holes in a plate, bounce off a light collimator that made the light look like it was from an infinite distance away, and be collected by the startracker camera. I added resistors and thermocouples to the startracker housing in order to heat the assembly and measure the temperature of individual components.

A typical test involved heating and then cooling the starcam assembly while recording images. Although the camera and the lightsource were stationary, the locations of the "stars" in the image sensor shifted over the course of the test due to the heat. With this information, I could calculate the change in star locations per degree Celcius.

Because startrackers operate with such high precision, the system was extremely sensitive, and I spent most of my summer debugging and validating the test setup. An example of 

ADD EXPLANATION OF BRACKET INSULATION WITH CHARTS OF EXPECTED BEHAVIOR

After thermally isolating the startracker from the testbed and ensuring the star motion data was valid, I could move on to isolating startracker components to identify which deformed the most with heat. As shown above, the star locations moved in repeatable directions and magnitudes. If the direction or magnitude of motion changes after rotating a startracker component, the motion can be attributed to that component. Using this approach, I identified the set of components that 




ADD DIAGRAM



How did I setup the test? diagram

Testing issues, etc

results and next steps