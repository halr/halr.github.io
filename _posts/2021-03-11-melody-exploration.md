---
title: "Week 6: Melody Exploration"
date: 2021-03-11
tags: mixd
---
**Pick a piece of music with an engaging melody and draw it.** *Engaging* is a very subjective term, but eleven year old me found the iconic five-note motif from the film [Close Encounters of the Third Kind](https://en.wikipedia.org/wiki/Close_Encounters_of_the_Third_Kind#Music) to be very engaging.

<iframe width="560" height="315" src="https://www.youtube.com/embed/AphKxQ2NsQo" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

The dialog in the film is very specific about the relation of the notes in the sequence.
> Give me a tone (Re to the second)\
Up a full tone (Mi to the third)\
Down a major third (Do to the first)\
Drop an octave (Do ...)\
Up a perfect fifth (So to the fifth)

In the traditional western musical notation, it's written thusly:

![](https://www.ars-nova.com/Theory%20Q&A/graphics/Q35.gif)

It is my understanding is that these intervals: octave; fifth; major third; and whole tone; are the first audible intervals encountered in [harmonics partials](https://www.ars-nova.com/Theory%20Q&A/Q35.html). Grounding this with the diatonic scale, I came up with this:

![](/images/ce3k.png)

Now let's imagine some interactive melodic experience based on this motif.

1) The easy one is an MIDI controller based on the big light board seen the background. I imagine it with light up interactive buttons, sending MIDI out to play notes and lighting up based MIDI recieved.
2) A glove that recognizes [John Curwen](https://en.wikipedia.org/wiki/John_Curwen)'s [Solfege](https://en.wikipedia.org/wiki/Solfège#Other_possibilities_to_denote_solfège) hand signs and translates the gesture to MIDI notes. An Arduino Nano 33 BLE Sense can be [trained to recognize gestures using TensorFlow lite](https://github.com/arduino/ArduinoTensorFlowLiteTutorials/tree/master/GestureToEmoji). The character in the foreground, played by François Truffaut, can be seen using them in the video above.