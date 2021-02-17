---
title: "Project #1: Redesigning Interaction, Part 2"
date: 2021-02-16
tags: intangible
---
Last week I analyzed an old project which made use capacitive proximity. Using the theory and framework for implicit interaction, illuminated the [short comings of the design]({% post_url 2021-02-10-redesigning-interaction %}). This week working with [Sean](https://szhu.github.io/itp-blog/), we redesign the interaction using a new sensor to improve usability.

The original project was an interactive exhibit that allows young users to explore how primary light colors mix together. The project&#39;s main drawback was that users did not understand that that they could interact with the system by bringing their hands close to the capacitive sensors but without the need to touching them.

For the redesign, we swap out the capacitive proximity sensors with a longer-range distance sensor and add cues that allow users to more easily understand the proper mode of interaction so that they can mix colors effectively.

The sensor we&#39;re using is the [Adafruit VL6180X Time of Flight Micro-LIDAR Distance Sensor Breakout](https://learn.adafruit.com/adafruit-vl6180x-time-of-flight-micro-lidar-distance-sensor-breakout/overview), which measures distances by illuminating the target with laser light and measuring the time the reflection of the light takes to return to the sensor. 

The sensor can measure in the range of 5 millimeters to 200mm, but a similiar sensor, the [VL53L0X Time of Flight Micro-LIDAR Distance Sensor](https://learn.adafruit.com/adafruit-vl53l0x-micro-lidar-distance-sensor-breakout) has a range of 50 to 1200 mm.

## Testing the Sensor

Using the [Adafruit Edge Badge](https://www.adafruit.com/product/4400) with a built in I2C *STEMMA* connector, I plugged in the sensor and loaded the example code provided by the library. The sensor outputs status and well as the measured distance. Interesting the sensor can detect the presense of a object beyond it's ability to measure the distance. Additionaly, the ability of the sensor to detect and objects expands out from the sensor in a cone. Understanding the status codes that represent, whether an object is detected and if it is within measuring range I mapped the measurement to the number of LEDs on the board as well as an audio tone. Since the original project involved color mixing, I also mapped the measurement to color blue.

<video width="720" height="406" controls>
  <source src="/images/vl6180x.mp4" type="video/mp4">
Video tag not supported.
</video>

## The Build

The build was fairly straightforward, but a few things needed to be adjusted.

The original Color Mixing project had 3 capacitative proximity sensors. For our demo we will  have one color variable and have the other two with fixed values. The value of red is fixed, mixing in blue gives colors from red to purple. The color change is hard to see, partly because the LEDs are not calibrated for perception. It is even harder to see over video call because camera kept changing the color balance as the color changed!

<video width="640" height="360" src="/images/colorMix3.mov">Video tag not supported.</video>
