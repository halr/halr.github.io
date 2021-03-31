---
title: "Explore Melody"
date: 2021-03-25
tags:  mixd
---
I wanted to explore the mathematical ratios that make up [just intonation](https://en.wikipedia.org/wiki/Just_intonation) with both audio and visuals. I was inspired by [Roger Antonsen](http://rantonse.no/en)’s [Metaphors, Mathematics, and the Imagination](https://www.ted.com/talks/roger_antonsen_math_is_the_hidden_secret_to_understanding_the_world) TED talk. In the talk he touches on how the ratio of four thirds is a [perfect fourth](https://en.wikipedia.org/wiki/Perfect_fourth).

I imagined a device that with a screen and two knobs that controlled the ratio. Output would be control voltage through a couple of jacks.

![device concept](/images/deviceConcept.png)

I prototyped the display and audio output in Processing. With the intention of translating it Max.

![four thirds](/images/fourThirds.png)

```Processing
import processing.sound.*;

float x = 0;
float y = 0;
float t = 0;

SinOsc baseOsc;
float baseFreq = 440.0; //hertz
SinOsc forthsOsc;

void setup() {
  background(255);
  size(500,500);
  
  fill(255,0,0);
  stroke(0);
  strokeWeight(3.0);
  
  // Create the oscillators and amplitudes
  baseOsc = new SinOsc(this);
  baseOsc.freq(baseFreq);
  baseOsc.play();
  
  forthsOsc = new SinOsc(this);
  forthsOsc.freq(baseFreq*(4/3)); // perfect forth
  forthsOsc.play();
  
  // The overall amplitude shouldn't exceed 1.0
  baseOsc.amp(0.5);
  forthsOsc.amp(0.5);
}

void draw() {
  translate(width/2, height/2);
  t = t + 0.01;
  x = cos(3*t);
  y = sin(4*t);
  
  stroke(255, (255 * x), (255 * y));
  ellipse((220 * x),(200 * y),4,4);
  
  float xAmp = map(x, -1.0, 1.0, 0, 0.5);
  float yAmp = map(y, -1.0, 1.0, 0, 0.5);
  baseOsc.amp(xAmp);
  forthsOsc.amp(yAmp);
}
```

I struggled deciding what aspect of the audio output to highlight, but settled changing the amplitude of the base note and it's perfect forth so that they are mixed as the graph draws. Overall, the sketch oscillates between the root note, A4 in this example, and it's perfect fourth: D5-ish. I'm still not sure about the method in which I mapped the negative values to get an amplitude value.
