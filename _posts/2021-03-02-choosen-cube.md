---
title: "Curious Rhythm Cube"
date: 2021-03-02
tags: intangible
---
Instead of narrowing down from [previous cube ideas]({% post_url 2021-02-23-curious-cube-ideas %}), I came up with a alternative concept. The Curious Rhythm Cube plays rhythm patterns which the user can control using simple gestures using the APDS9960 gesture sensor.

![idea sketch](/images/rhythmBox.png)

## Intangible Interaction
The Curious Rhythm Cube does not provide any designated physical controls, but is meant to be interacted with intangibly without any physical contact. The Curious Rhythm Cube plays a number of increasing complex rhythm patterns that the user can cycle through. Visual feedback is given by 16 LED ring, which lights up the subdivision of the beat as it plays. A simple metronome like pattern would appear to oscillate back and forth.
![metronome](/images/metronome.png)

By gesturing left and right, the rhythm patterns can be cycled back and forth. The user can also control the tempo by gesturing forward and backwards.
![interaction map](/images/interactionMap.png)

Another possibility is mapping proximity to note velocity, or as a wake event for the cube. This will be explored during prototyping.

## System Design Options
I have identified three possible system designs that might work. In all three case the sequencing of the rhythm patterns would happen on the microcontroller.
* An [Arduino Nano BLE Sense](https://store.arduino.cc/usa/nano-33-ble-sense) microcontroller sending [MIDI over USB](https://www.arduino.cc/en/Reference/MIDIUSB)
* [Arduino MKR1000 WiFi](https://store.arduino.cc/usa/arduino-mkr1000), with the [Sparkfun APDS-9960 breakout](https://www.sparkfun.com/products/12787), sending [OSC](https://github.com/CNMAT/OSC) over WiFi to Ableton Live with [Connection Kit](https://www.ableton.com/en/packs/connection-kit/)
* [Sparkfun MIDI Shield](https://learn.sparkfun.com/tutorials/midi-shield-hookup-guide), also with the [Sparkfun APDS-9960 breakout](https://www.sparkfun.com/products/12787), sending MIDI directly to a Sound Module using standard MIDI cables

## BOM
Bill of Materials

| Item | Price | Purpose and/or notes |
|-----|------|-----|
| white semitranslucent acrylic | NA | cube structure |
| [Arduino Nano BLE Sense](https://store.arduino.cc/usa/nano-33-ble-sense) | $31.10 | Potentially another microcontroller? |
| NeoPixel Ring | NA | in stock |
| [Ableton Live](https://www.ableton.com) with [Max for Live](https://www.ableton.com/en/live/max-for-live/) | [90 day trail](https://www.ableton.com/en/trial/) | audio output |

## Project Timeline

| Due Date | Action |
|---------|-------|
| March 3rd | Idea Show & Tell |
| ~ March 5th | prototyping and system decision |
| ~ March 7th | cube construction |
| ~ March 13th | implementation |
| ~ March 15th | testing |
| March 17th | Project Presentation |
