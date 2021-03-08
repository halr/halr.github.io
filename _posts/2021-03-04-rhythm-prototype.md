---
title: "Week 3+4+5: Rhythm Exploration & Prototype"
date: 2021-03-04
tags: mixd
published: false
---
Intro

## Rhythm Interaction Designs
Design several interactions that focus on exploring rhythm / time grids.

## Prototyping Gesture Rhythm Patterns
I chose to prototype controlling rhythm patterns with gestures. Using waving left and right gestures rhythm patterns are increasing complexity are played. I created eight rhythm patterns in Ableton Live, ranging from a metronome pattern to a basic blue/rock grove to a more funky complex pattern. The patterns increase in complexity building on the patterns. Here are three representative patterns.
![](/images/rhythmTikTik.png)
![](/images/rhythmBlues.png)
![](/images/rhythmZigZag.png)

### Testing Arduino OSC to Ableton Live
Week 3's assignment was to add control via MIDI, OSC, or Max for Live to an aspect of Abelton meant for interaction. I did not have a satisfactory solution then, but my explorations of Arduino generated OSC messages were succesful, so I'll document them here. I used the WiFi capable [Arduino MKR1000](https://store.arduino.cc/usa/arduino-mkr1000) with the [WiFi101](https://www.arduino.cc/en/Reference/WiFi101) and [OSC](https://www.arduino.cc/reference/en/libraries/osc/) libraries. The MKR1000 sends gestures messages that are recieved by an Max 4 Live patch.

Before hooking up a gesture sensor, I tested sending OSC messages over WiFi [UDP](https://en.wikipedia.org/wiki/User_Datagram_Protocol). The following sketch sends a OSC message every three seconds. The format of the OSC message is any example of the gesture messages I intend to send once the [ADPS9600 gesture sensor](https://www.sparkfun.com/products/12787) is incorporated.
```C++
#include <SPI.h>
#include <WiFi101.h>
#include <WiFiUdp.h>
#include <OSCMessage.h>

WiFiUDP Udp;
// ... other declarations removed for brevity

void setup() {
  // attempt to connect to WiFi network:
  while ( status != WL_CONNECTED) {
    // Connect to WPA/WPA2 network:
    status = WiFi.begin(ssid, pass);
    // wait 10 seconds for connection:
    delay(10000);
  }
  Udp.begin(localPort);
}

void loop() {
  OSCMessage msg("/gesture");
  msg.add("right");
  Udp.beginPacket(outIp, outPort);
  // send the message:
  msg.send(Udp);
  // mark the end of the OSC Packet:
  Udp.endPacket();
  delay(3000);
}
```
On the recieveing end, I created a test patch that [route](https://docs.cycling74.com/max8/refpages/route)s gestures received as [udpreceive](https://docs.cycling74.com/max8/refpages/udpreceive) messages. The [buttons](https://docs.cycling74.com/max8/refpages/button) blink indicating that a message has been and routed, or not for debugging. The intention is have left and right gestures cycle through the set of rhythm clips and the up and down gestures increase and decrease the tempo.
![](/images/oscGestures.png)

### Adding Live Paths
The next step is adding live paths