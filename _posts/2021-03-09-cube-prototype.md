---
title: "Rhythm Cube Prototyping"
date: 2021-03-09
tags: intangible mixd
---
This week we prototype the transport and communication aspects of the [Curious Rhythm Cube]({% post_url 2021-03-02-chosen-cube %}). Should the cube handle the sequencing of the rhythms itself sending MIDI data through USB or BLE? Should the cube send only to gesture events to a sequencer, such as Abelton Live, over OSC?

## Arduino and MIDI USB Library
My first choice was to try using the [Arduino Nano 33 BLE Sense](https://store.arduino.cc/usa/nano-33-ble-sense) since it includes the ADPS9600 gesture sensor on board. I reviewed the [MIDI Output using an Arduino](https://itp.nyu.edu/physcomp/labs/labs-serial-communication/lab-midi-output-using-an-arduino/) lab from ITP's Physical Computing class. Unfortunately, the [MIDIUSB library](https://www.arduino.cc/en/Reference/MIDIUSB) does not compile error against [mbed](https://os.mbed.com) based Nano BLE 33 Sense board.
```
WARNING: library MIDIUSB claims to run on avr, sam, samd architecture(s) and may be incompatible with your current board which runs on mbed architecture(s).
#error MIDIUSB can only be used with an USB MCU.
#error "Unsupported architecture"
```
Fortunately, MIDIUSB does compile and work on the SAMD based [Arduino MKR1000](https://store.arduino.cc/usa/arduino-mkr1000) board. Sure enough, once I open Ableton Live, drop in an instrument, I heard notes being played. An alternative to the MIDIUSB library is the [47 Effects MIDI Library](https://github.com/FortySevenEffects/arduino_midi_library). Rather than exploring this alternative, I decided to look a couple of wireless options.

## MKR1000 to Abelton Live using OSC
I also successfully programmed the Arduino MKR1000 to send gesture based OSC messages over WiFi UDP. This is covered in my ***MIxD*** post: [Week 3+4+5: Rhythm Exploration & Prototype]({% post_url 2021-03-04-rhythm-prototype %}).

## Nano BLE 33 Sense using MIDI BLE
I followed Tom Igoe's [MIDI over Bluetooth LE](https://tigoe.github.io/SoundExamples/midi-ble.html) example plays plays the first section of Steve Riech's [Piano Phase](https://en.wikipedia.org/wiki/Piano_Phase) as MIDI using the [ArduinoBLE library](https://www.arduino.cc/en/Reference/ArduinoBLE). Using MIDI sequenced on the Arduino and sending those messages over Bluetooth, might be the most flexible solution. Using this example as a basis for the Curious Rhythm Cube, I would have to change the timing to use [`millis()`](https://www.arduino.cc/reference/en/language/functions/time/millis/) rather than [`delay()`](https://www.arduino.cc/reference/en/language/functions/time/delay/) in order to incoporate reacting to the sensor readings. 

## The MIDI Cable option
Lastly one option not explored but certainly worth considering is using the original [standard MIDI connector](https://en.wikipedia.org/wiki/MIDI#Connectors). The [Sparkfun MIDI Shield](https://www.sparkfun.com/products/12898) provides the required circuitry. Using standard MIDI cables would allow replacing a computer with a stand alone MIDI module. 