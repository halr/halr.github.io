---
title: "Curious Rhythm Cube"
date: 2021-03-17
tags: intangible mixd
---
***Work in Progress:*** The Curious Rhythm Cube is an instrument that lets play with rhythm. You alter the tempo and the patterns by the wave across the top of the cube. MIDI is sent wirelessly over Bluetooth to Ableton Live. For fun the drum kit used in Ableton is the *Impulse 808* based on the 80's [Roland TR-808](https://en.wikipedia.org/wiki/Roland_TR-808).

## Wiring up the hardware
The hardware consists of an [Arduino Nano 33 BLE Sense](https://store.arduino.cc/usa/nano-33-ble-sense) with integrated APDS9960 gesture sensor and Bluetooth LE module, a 16  LED Ring, and small LiPo battery as the power supply.

## Software
The software was created using the Arduino IDE, and uses three libraries: the [Adafruit NeoPixel](https://www.arduino.cc/reference/en/libraries/adafruit-neopixel/); [Arduino APDS9960](https://www.arduino.cc/reference/en/libraries/arduino_apds9960/); and [ArduinoBLE](https://www.arduino.cc/en/Reference/ArduinoBLE).
The sketch keeps time based on the duration of a sixteenth note, which is based on an internal *beats per minutes* value. This tempo  can be altered by a gesture. Gestures are read every time through the loop, but note evaluation only happens after the sixteenth note duration has lapse. Then if the bluetooth connection is available, it either stop a previous note, plays a new note, or both. When a note is played, the note is mapped to unique color, and the corresponding LED on the ring is lit up. The rhythm patterns or sequences are stored internally, and currently playing pattern can be cycled through with a gesture.

The source code will be made available on GitHub soon!

![Test Jig](/images/testJig.png)

## Cube construction
*coming soon!*

![Test Jig](/images/whiteCube.png)

## Putting it all together
Since the cube generates MIDI messages it need to be connected to something that can receive MIDI messages over Bluetooth. I'm using [Ableton Live](https://www.ableton.com/en/live/).