---
layout: page
title: Solar Sail Photos to Models
time: Fall 2020
description: NASA MSFC, Guidance & Navigation Design Team
img: assets/img/lightsail2.jpg
importance: 4
category: work
---

## Overview
During my internship at NASA MSFC in the fall of 2020, I assisted in validating control models for NASA's solar sails NEA Scout and Solar Cruiser. My project investigated the validation of the sail thrust model using the Planetary Society's LightSail-2, which is currently in low Earth orbit.

When a solar sail deploys in space, it does not do so perfectly in a flat plane. This billowing effect creates off-nominal thrust vectors. In order to accurately validate the thrust model using flight data, we needed an accurate FEA model of LightSail-2 that captures this behavior.


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/lightsail2.jpg" title="solarsail" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Image of LightSail-2 taken on its camera (image source: the Planetary Society)
</div>


## Contributions
Using MATLAB, I developed a system to create a mesh of the sail that accurately characterized its billowing distortion from photos taken by the camera mounted on the sail. I incorporated the Inverse Perspective Algorithm, which was developed to find the attitude difference between two vehicles for automated docking. By dividing the sail up into triangular elements, the IPA calculated the angle of these elements out-of-plane with respect to the flat plane of the ideal sail. These angles, in the form of a normal vector, would be found for each element, along with the relative locations of the nodes. An accurate mesh could then be formed with this information.

I finished my internship before I was able to complete the project. However, I meticulously documented my ideas and work, so the next intern could take up the project where I left off.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/sailimage_to_model.png" title="sailmodel" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This process could create and FEA model of LightSail-2 based on an photo from orbit. The model could then be used for thrust model validation.
</div>

