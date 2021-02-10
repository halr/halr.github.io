---
layout: post
title: "Project #1: Redesigning Interaction, Part 1"
date: 2021-02-10
tags: intangible
---

I have been interested in intangible interaction for quite a while. As part of my art practice, my partner and I design wearable tech couture art pieces, some which used intangible interaction based accelerometer data or bluetooth radio proximity.  In 2019, we were invited by a local science museum to be a part of thier community outreach program. We wanted to showcase our dresses as well as have an education activity. Since our dresses incorporate addressable LEDs, we choose to demonstrate RGB color mixing. Having been experimenting with capacitive proximity sensing, we thought it might be fun to make it into an interactive activity. The idea was that attendees could position thier hands over three capactive sensors and mix colors on a half size mock up of one of dresses. We created an enclosure, went to the event, and set up the display. 

![the set up](/images/IMG_7156.jpeg)

The design failed, people didn't what to do or where to look for the effect. We end up putting a hand written sign explaining what to do and where to look. This isn't a non-intangible interaction that I want to replace with intangible interaction, but a poorly designed intangible interaction that I wish to replace with a better intangible interaction.

![bad design](/images/IMG_7158.jpeg)

In hindsight, it's easy to see how the set up failed. The etched hand print indicated to every child to slam thier hand on it. Looking down, attendees failed to see the lights on the dress form reacting, the interaction faded to the background. The sensitivty of the capacitive proximity sensor was limited to near distances of about a foot away from the electrode.

![interaction diagram](/images/IMG_4679.png)

Technically, the system used the Bare Conductive [Touch Board](https://www.bareconductive.com/shop/touch-board/) with a built-in proximity capacitive touch sensor controller in the [MPR121 chip](https://cdn-shop.adafruit.com/datasheets/MPR121.pdf). The Bare Conductive Touch Board is programmed using the Arduino IDE *(sketch to uploaded to github soon)*. The three electrodes are made with cooper tabe on heavy paper. The enclouse is laser cut and engraved MDF and acrylic. The three electrodes are placed under the acrylic. You can see we experimenting with interactively mixing colors [here](https://www.instagram.com/p/BvzP8GUn6hn/).
