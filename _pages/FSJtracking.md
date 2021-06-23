---
layout: single
title: "FLSJ tracking project"
permalink: /FSJtracking/
header:
    overlay_image: /assets/images/jay3.JPG
author_profile: true
toc: true
toc_label: "Sections"
toc_icon: "crow"
classes: wide
date: March 12, 2021
---

### Overview of Florida scrub-jay Tracking Project 

To collect constant movement data from Florida scrub-jays, we have deployed an automated movement tracking system developed by [Cellular Tracking Technologies](https://celltracktech.com/){:target="_blank" rel="noopener"}. 

{% include figure image_path="/assets/images/watertower2.jpg" alt="" caption="" %}

#### How it works

The CTT automated tracking system utilizes a combination of [sensor stations](https://celltracktech.com/products/tag-system/ctt-sensorstation/){:target="_blank" rel="noopener"} and a grid of [receivers nodes](https://celltracktech.com/products/tag-system/ctt-node/){:target="_blank" rel="noopener"} that pick up signals emitted from [LifeTags](https://celltracktech.com/products/tag-system/lifetag/){:target="_blank" rel="noopener"}. LifeTags are lightweight at ~0.45g which is less than 1% of our study system's average body mass. 
{% include figure image_path="/assets/images/gif1.gif" alt="" caption="" %}

The resulting data comprise of Tag ID, node ID, date and time, and signal strength (RSSI). These are then fed into a localization algorithm developed by CTT (or custom if you choose) which the R script can be found [here](https://cellular-tracking-technologies.github.io/localization-methods.html){:target="_blank" rel="noopener"}. Essentially the code does a type of triangulation using the relationship between distance and RSSI to obtain a location estimate. 

{% include figure image_path="/assets/images/rssi.png" alt="" caption="" %}


### Set up at Archbold
<figure style="width: 400px" class="align-right">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/ctt1.jpg" alt="">
  <figcaption>Antennas for the sensor station were intalled on top of the water tower (see top).</figcaption>
</figure> <br> 

#### Installation and setup
We first installed 3 yagis and 1 omnidirectional antenna at the top of our 140 ft water tower to maximize coverage. The sensor station was placed at the bottom for easy maintenance and access to an outlet and we connected it to the antenna using coax cable. We used a surge protector from APC because that outdoor outlet was prone to failure and disrupting data collection. The initial version of the sensor station had to be downloaded manually with a USB -- luckily this is fixed now and all the data is uploaded via wifi every hour! 

We then deployed 42 nodes throughout Archbold to test out the system (more details below). Nodes were placed on a 10 ft conduit pole that were slid over a 2 ft rebar that was pounded into the ground for stability. About 1 ft of the conduit overlapped with the rebar, which was enough to keep the nodes steady. The farthest node was 2.33 km from the sensor station while the closest was 1.18 km away. 

<figure style="width: 400px" class="align-right">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/ctt6.png" alt="">
</figure> <br> 

#### Tags
We tagged 10 nonbreeding Florida scrub-jays with LifeTags. LifeTags came pre-attached to a 3D-printed plastic tab that had pre-drilled holes. We used 1.0 mm Stretch Magic string to make leg loops as past work using VHF tags showed that our birds react poorly to backpack-style tags. We made leg loops based on a [Naef-Daenzer 2007](https://onlinelibrary.wiley.com/doi/10.1111/j.2007.0908-8857.03863.x){:target="_blank" rel="noopener"} and made multiple-sized tags in the lab based on range of weights of our birds. While we could have opted to make the tags in the field, we were short-staffed so this was the easiest approach. However, there is a new paper by [Jirinec et al. 2021](https://onlinelibrary.wiley.com/doi/epdf/10.1111/jofo.12353){:target="_blank" rel="noopener"} that we are considering using for this season. 

Florida scrub-jays were captured by using drop traps baited with peanuts. Immediately after capture, we weighed the birds to fit the correctly sized tag. We fit them so that the leg loops were snug but not too tight, and there was room for the tip of a finger to go through when the leg loop was stretched. Once the tag was equipped, we used the handheld locator to make sure the signals were transmitting properly. After releasing the bird, we monitored its behavior for at least 10 minutes. We did not see any visible signs of stress as tagged birds quickly resumed normal behavior of flying, foraging, and feeding young. None of our tagged birds got caught or were restricted due to the tags. 

{% include figure image_path="/assets/images/ctt7.png" alt="" caption="" %}


### Pilot test
#### Overview
We installed a pilot grid in a small section of the study tract in spring of 2019. We installed a 6 x 7 grid (42 nodes) at 200m intervals per CTT's recommendations. 

In the winter, we ran a pilot test to test how well our tags were doing. 

#### Results


### Problems & troubleshooting



### Future directions

