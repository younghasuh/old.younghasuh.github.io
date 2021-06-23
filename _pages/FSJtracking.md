---
layout: single
title: "FLSJ tracking project"
permalink: /FSJtracking/
header:
    overlay_image: /assets/images/jay5.JPG
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

<br>

#### How it works

The CTT automated tracking system utilizes a combination of [sensor stations](https://celltracktech.com/products/tag-system/ctt-sensorstation/){:target="_blank" rel="noopener"} and a grid of [receivers nodes](https://celltracktech.com/products/tag-system/ctt-node/){:target="_blank" rel="noopener"} that pick up signals emitted from [LifeTags](https://celltracktech.com/products/tag-system/lifetag/){:target="_blank" rel="noopener"}. LifeTags are lightweight at ~0.45g which is less than 1% of our study system's average body mass. 
{% include figure image_path="/assets/images/gif1.gif" alt="" caption="" %}

The resulting data comprise of Tag ID, node ID, date and time, and signal strength (RSSI). These are then fed into a localization algorithm developed by CTT (or custom if you choose) which the R script can be found [here](https://cellular-tracking-technologies.github.io/localization-methods.html){:target="_blank" rel="noopener"}. Essentially the code does a type of triangulation using the relationship between distance and RSSI to obtain a location estimate. 

{% include figure image_path="/assets/images/rssi.png" alt="" caption="" %}

<br>

### Set up at Archbold
#### Installation and setup

<figure style="width: 400px" class="align-right">
  <img align = "right" src = "/assets/images/ctt0.jpg">
</figure>


We first installed 3 yagis and 1 omnidirectional antenna at the top of our 140 ft water tower to maximize coverage. The sensor station was placed at the bottom for easy maintenance and access to an outlet and we connected it to the antenna using coax cable. We used a surge protector from APC because that outdoor outlet was prone to failure and disrupting data collection. The initial version of the sensor station had to be downloaded manually with a USB -- luckily this is fixed now and all the data is uploaded via wifi every hour! 

We then deployed 42 nodes throughout Archbold to test out the system (more details below). We used a sub-meter Trimble to place the nodes as accurately as possible. Nodes were attached to the tip of a 10 ft conduit pole that was slid over a 2 ft rebar pounded into the ground for stability. About 1 ft of the conduit overlapped with the rebar, which was enough to keep the nodes steady. The farthest node was 2.33 km from the sensor station while the closest was 1.18 km away. 

{% include figure image_path="/assets/images/ctt6.png" alt="" caption="" %}


#### Tags
We tagged 10 nonbreeding Florida scrub-jays with LifeTags. LifeTags came pre-attached to a 3D-printed plastic tab that had pre-drilled holes. We used 1.0 mm Stretch Magic string to make leg loops as past work using VHF tags showed that our birds react poorly to backpack-style tags. We made leg loops based on a [Naef-Daenzer 2007](https://onlinelibrary.wiley.com/doi/10.1111/j.2007.0908-8857.03863.x){:target="_blank" rel="noopener"} and made multiple-sized tags in the lab based on range of weights of our birds. While we could have opted to make the tags in the field, we were short-staffed so this was the easiest approach. However, there is a new paper by [Jirinec et al. 2021](https://onlinelibrary.wiley.com/doi/epdf/10.1111/jofo.12353){:target="_blank" rel="noopener"} that we are considering using for this season. 

Florida scrub-jays were captured by using drop traps baited with peanuts. Immediately after capture, we weighed the birds to fit the correctly sized tag. We fit them so that the leg loops were snug but not too tight, and there was room for the tip of a finger to go through when the leg loop was stretched. Once the tag was equipped, we used the handheld locator to make sure the signals were transmitting properly. After releasing the bird, we monitored its behavior for at least 10 minutes. We did not see any visible signs of stress as tagged birds quickly resumed normal behavior of flying, foraging, and feeding young. None of our tagged birds got caught or were restricted due to the tags. 

{% include figure image_path="/assets/images/ctt7.png" alt="" caption="" %}


<br>

### Pilot test
#### Experimental design
We installed a pilot grid in a small section of the study tract in spring of 2019. We installed a 6 x 7 grid (42 nodes) at 200m intervals per CTT's recommendations. In the winter, we ran a pilot test to test how well our tags were doing by placing tags on a platform and placing them next to nodes. 

We had 2 sets of 4 tags and 1 set of 2 tags that were placed on a rotating and stationary platform, respectively. We had the 2 sets rotate either horizontally or vertically to simulate movement. We picked 4 nodes to experiment with, each differing in regards to vegetation height and density so we had a 4x4 treatment. Platforms were placed next to the node at 15 minute intervals, at different rotational directions (or stationary) and also at different heights (ground - 1.5m high - 3m high). Times and treatment were recorded as well as a distance and bearings of the actual platform location to the node.

Using the localization algorithm, we used 1 minute localization averages spanning 15 minutes (thus 15 data points) and compared them with the actual location using distances and this was visualized using minimum convex polygons. 


#### Results
<figure style="width: 400px" class="align-right">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/ctt8.png" alt="">
</figure> 

Overall, we got pretty decent coverage by our nodes, as you can see in these figures. These show a graphical representation of the data: each letter and red triangle represent a node. The pink X indicates the actual location a tag was placed whereas the black circle shows its estimated location. The colorful circles around the nodes depict signal strength, i.e., larger circles represent weaker signals whereas smaller circles depict stronger signals (colors are matched by signal strength but unimportant here). The top two figures show that the majority of nodes are picing up the signal of this one tag and the location estimates match pretty well with the actual location. The bottom two figures show a different story, however, with only a few - sometimes even one! - nodes picking up the tag location at pretty low signal strengths and thus creating strong discrepancies between the estimated and actual location. The bottom right figure doesn't even show an estimated location because only 1 node picked it up, meaning the tag could be anywhere in that radius. 

{% include figure image_path="/assets/images/ctt9.png" alt="" caption="" %}

When looking at the localizations, they were *not great*, especially depending on where the tag was placed. On average, the localization error, calculated by the average distance between the actual and estimated locations, was **117.56 (SE +/- 1.74) m**. Accuracy was highly affected by node height, with tags closer to the ground being more accurate than tags higher up. This result seems counter intuitive but this has to do with the node coverage you saw above: tags that were higher up got detected by so many more nodes, it would even bias the location estimate. Coupled with the fact that vegetation can actually obscure signal transmission, we saw a strong bias towards more open habitat. CTT has been working on improving this localization algorithm and the current algorithm (as of March 2021) has reduced the error to **73.83 (+/- 3.48 m)**. This is still far from ideal but we are hoping to update the algorithm to our system to lower this error. 

{% include figure image_path="/assets/images/ctt10.png" alt="" caption="Maps showing minimum convex polygons (MCPs) of localization estimates overlayed on top of a satellite image. Each tag is represented by colored points and MCP while the white stars indicate node locations. The node where the tags were placed next to is indicated in a semitransparent white circle (overlapped in first image). Each panel is from a 15-min experimental trial conducted on the ground, 1.5m up, and 3m up. The MCPs grow larger and become less accurate the higher up the tags are. This effect is also biased towards the southwest where the habitat is more open." %}

<br>

### Problems & troubleshooting

In addition to the current accuracy issues, there are a few more hurdles that we need to overcome. 

#### 1. Data management

This system generates a LOT of data - about 5 MB of raw data per day (tag, node health, node GPS data) so a good storage system is key. Especially if you are to store the raw and processed data (the latter is much larger), this can be an issue. Both raw and processed data will be saved at Archbold for future use. In addition, this system requires familiarity with R and Github. CTT is in the process of developing an R package soon, however. 

#### 2. Tabs and tags
<figure style="width: 300px" class="align-right">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/ctt5.jpg" alt="">
</figure> 

We had so many tag problems from the start. We first made the mistake of using Stretch Magic that was too thin. Upgrading to the 1.0 mm helped and we still have not lost tags this way, and plus there seem to be no signs of abrasian on the skin. The next few batches of LifeTags we received came faulty or flimsy. We lost so many tags in this process, it was a pain to re-trap the birds and retrieve the tags. Because they are solar-powered, about 30-40% were never retrieved, possibly due to them being flipped over or having their solar panel covered. In the latter batches we manually fortified our tags using epoxy to strengthen the bond between the tag and plastic tab. However, we still experienced tag losses through antennas breaking off, which we are unsure why this happens. While Florida scrub-jays do have strong bills, this antenna-loss was also observed in tagged tree swallows, which makes us question if it was actually the birds breaking off the antennas. Regardless, I highly advise anyone using these tags to take extra precautions in strengthening their tags. 

#### 3. Other hardware issues
<figure style="width: 300px" class="align-right">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/ctt11.png" alt="">
</figure> 

We noticed that after a while, our receiver nodes began developing a white crust on their solar panels that seem to reduce their charging capacity. The identity of this substance is unclear as we don't observe it on any of our buildings, vehicles, or even solar panels so it must be some interaction between the panel epoxy, heat, and rain. We found that we can remove it using rubbing alcohol but it means that we need to service these devices regularly to ensure high data quality. 

I also highly recommend checking all your nodes prior to deployment as we had a few that came with faulty software and needed to be synced or returned. Because there is a long wait time for the equipment to ship, I advise you order extra equipment to account for faulty products. 

<br>

### Future directions

We already increased the grid to entire study tract by adding over 100 nodes and 4 additional sensor stations. The new node array has 355m inter-node distances based on how well the previous grid was doing. 

I will continue to work on improving the localization algorithms so that it will reach an acceptable level of error for the type of questions I want to ask. I will also be conducting additional calibration tests in the field this summer to support this. 

Ultimately, I will use the generated location data to analyze movement, habitat use, and possibly social networks of my birds. 

<br>

### Acknowledgements

This project would not have been made possible without the support of the following: Cornell Lab of Ornithology Athena Fund, American Ornithological Society, American Society of Naturalists, Florida Ornithological Society, Wilson Ornithological Society, Animal Behavior Society, and Archbold Biological Station. 	

{% include figure image_path="/assets/images/ack.png" alt="" caption="" %}
