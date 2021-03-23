---
title: "Curious Rhythm Cube"
date: 2021-03-17
tags: intangible mixd
---
***Work in Progress:*** The Curious Rhythm Cube is an instrument that lets play with rhythm. You alter the tempo and switch between the patterns by the wave across the top of the cube. It is essential a gesture controlled 16 step sequencer with 6 hardcoded patterns which sends MIDI messages wirelessly over Bluetooth. For my demo, I am using Ableton Live to receive the MIDI messages. Just for fun, the drum kit used in Ableton is the *Impulse 808* based on the 80's [Roland TR-808](https://en.wikipedia.org/wiki/Roland_TR-808) drum machine.

## Wiring the hardware
![image of interior](/images/cubeInterior.png)

The hardware consists of an [Arduino Nano 33 BLE Sense](https://store.arduino.cc/usa/nano-33-ble-sense) with an integrated APDS9960 gesture sensor and Bluetooth LE module, a 16  LED Ring, and a small LiPo battery and switch as the power supply. Since I wanted to mount the Nano at the top of the cube, I used jumper wires to the headers on the Nano. The **VIN** pin accepts between 5-21 volts. Since **VIN** is next to a **GND** pin, I used a small adapter cable with a switch and a [JST RCY connector](https://en.wikipedia.org/wiki/DC_connector#JST_RCY_connector) that matches the pitch of the headers on the board.

![image of battery cable](/images/powerCable.png)

## Software
The software was created using the Arduino IDE, and uses three libraries: [Arduino APDS9960](https://www.arduino.cc/reference/en/libraries/arduino_apds9960/); [Adafruit NeoPixel](https://www.arduino.cc/reference/en/libraries/adafruit-neopixel/); and [ArduinoBLE](https://www.arduino.cc/en/Reference/ArduinoBLE).
The sketch keeps time based on the duration of a sixteenth note, which is based on an internal *beats per minutes* value. This tempo  can be altered by a gesture. Gestures are read every time through the loop, but note evaluation only happens after the sixteenth note duration has lapse. Then if the bluetooth connection is available, it either stop a previous note, plays a new note, or both. When a note is played, the note is mapped to unique color, and the corresponding LED on the ring is lit up. The rhythm patterns or sequences are stored internally, and the currently playing pattern can be cycled through with a gesture. The [source code](https://github.com/halr/curious_rhythm_cube) is available on GitHub!

![image of hardware](/images/testJig.png)

## Cube construction
*coming soon!*
- [ ] progress images/videos with descriptions, 
- [ ] reflections,

![image of cube](/images/whiteCube.png)

## Putting it all together
Since the cube generates MIDI messages it need to be connected to something that can receive MIDI messages over Bluetooth. I'm using [Ableton Live](https://www.ableton.com/en/live/).
- [ ] final outcome (whether the project is finished or not), 

## Going Further
If I had more time, there are a number of possible improvements that could be made. Some in construction, like using screws rather than hot glue, but expanding the MIDI programming and handling the gesture sensitivity would certainly improve the project. 

With the Arduino hot glued in place at the inside top of the cube, there is not much room to attach a USB cable for additional programming. On some Bluetooth enabled boards it is possible to program the board wireless, but after a bit of research it does not appear to be so with the Arduino Nano 33 BLE.

The cube has a couple of MIDI limitations, left out for lack of time. The rhythm sequences are all monophonic in the sense that only one note is defined for each step. Most rhythm patterns in western music are polyphonic in nature. It would not be hard to add polyphony, just more code. Additionally, notes are turned off (in the MIDI sense) at the next step because note duration is not defined. Notes are also not accented, in MIDI terms there are played at the same velocity. It would not be hard to adjust the note velocity at the beats in the measure.

Lastly, after the failure in the demo for the cube to recognize gestures possibly due to a change in light conditions. I wonder if this might not be an opportunity to use machine learning to train a model to adjust gesture sensitivity based on the ambient light reading from the same sensor.