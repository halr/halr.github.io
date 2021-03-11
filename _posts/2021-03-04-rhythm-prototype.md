---
title: "Week 3+4+5: Rhythm Exploration & Prototype"
date: 2021-03-04
tags: mixd
---
This is a big catch up post, where I cover serval things, including explore adding external control to Ableton Live, brainstorming rhythm interaction designs and prototyping a design. In previous weeks, I felt I was attempting too much without a basic understanding of Ableton Live. I am much more confident in my ability to prototype using Ableton now.

## Rhythm Interaction Designs
The assignment for weeks 4 and 5 was to design several interactions that focus on exploring rhythm / time grids.
* The **Curious Rhythm Cube** is melding of designing a rhythm interaction and an intangible interaction with the form of a cube. The [Curious Rhythm Cube]({% post_url 2021-03-02-choosen-cube %})'s interaction allow for the exploration of rhythm in terms of tempo and complexity. Rather than a time grid, a 16 LED ring at the top of the cube reflects the circular nature of the repeating pattern. An LED lights up if there is a note being played at the corresponding sub division. A gesture sensor can recognize the wave of a hand along two axes: Left & Right, Up & Down. A wave on the Up & Down axis controls the tempo of the pattern, and a wave in the Left & Right axis controls the rhythm pattern being played.
![](/images/rhythmCube.png) 
* **Firefly Syncing Rhythm** is inspired Steve Riechs's [*phasing*](https://en.wikipedia.org/wiki/Phase_music) technique and fireflies' synchronization of thier flashing. Years ago, I came across a simple [algorthmic explaination of how fireflies synch up](https://ncase.me/fireflies/), by nudging thier internal flashing clocks forward when they see a nearby firefly flash. I can image folks wearing cute firefly badges that make simple beeps that gradually synch up over time. The *flashing* can be made by infrared transmitter and receivers. There is even a MakeCode BBC Micro Bit [firefly example](https://makecode.microbit.org/projects/fireflies), which uses the Bluetooth radio.

## Prototyping Gesture Rhythm Patterns
I am choosing to prototype controlling rhythm patterns with gestures of the Curious Rhythm Cube. Using waving left and right gestures rhythm patterns are increasing complexity are played. I created eight rhythm patterns in Ableton Live, ranging from a metronome pattern to a basic blue/rock grove to a more funky complex pattern. The patterns increase in complexity building on the patterns. Here are three representative patterns.
![](/images/rhythmTikTik.png)
![](/images/rhythmBlues.png)
![](/images/rhythmZigZag.png)

### Testing Arduino OSC to Ableton Live
Week 3's assignment was to add control via MIDI, OSC, or Max for Live to an aspect of Abelton meant for interaction. I did not have a satisfactory solution then, but my explorations of Arduino generated OSC messages were succesful, so I'll document them here. I used the WiFi capable [Arduino MKR1000](https://store.arduino.cc/usa/arduino-mkr1000) with the [WiFi101](https://www.arduino.cc/en/Reference/WiFi101) and [OSC](https://www.arduino.cc/reference/en/libraries/osc/) libraries. The MKR1000 sends gestures messages that are received by an Max 4 Live patch.

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
On the receiving end, I created a test patch that [routes](https://docs.cycling74.com/max8/refpages/route) gestures received as [`udpreceive`](https://docs.cycling74.com/max8/refpages/udpreceive) messages. The [`button`](https://docs.cycling74.com/max8/refpages/button)s blink indicating that a message has been and routed, or not for debugging. The intention is have left and right gestures cycle through the set of rhythm clips and the up and down gestures increase and decrease the tempo.

![](/images/oscGestures.png)

### Adding Live Paths
OSC messages being received and routed, it was time to cycle through clips using [`live.path`](https://docs.cycling74.com/max8/refpages/live.path) and [`live.object`](https://docs.cycling74.com/max8/refpages/live.object). I am struggeling to get a clip triggered.

![](/images/oscLivePath.png)

### Arduino & MIDI
Lastly, I also explored using Arduino sending MIDI via USB and BLE. A bit of this is documented in my [Rhythm Cube Prototyping]({% post_url 2021-03-09-cube-prototype %}) post.