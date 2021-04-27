---
title: "Conductive Melody Progress Report"
date: 2021-04-22
tags:  mixd
---
***Work in Progress:*** I created a little inspirational video of Conductive Melody. I call it inspirational, because it is not a recored performance. At the event, due loss of connectivity, the reference model was not downloaded and the system failed. I created the audio track for the video as a mood piece, indicating the desired result.

I created a repeating sub bass line based on an example pattern from the [Teenage Engineering](https://teenage.engineering/_img/565eeff1d24bc70300c8a69f_original.pdf). I then took the example pattern from the same source and  ran it through the Ableton Live Plugin [Magenta Studio](https://magenta.tensorflow.org/studio/ableton-live)'s  [Continue](https://magenta.tensorflow.org/studio/ableton-live#continue) tool for the number measures to get me a one minute piece.

<iframe width="560" height="315" src="https://www.youtube.com/embed/NLyYvI9Qm90" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## The Plan
1. Create a [Node.js](https://nodejs.org/en/) app to run [Piano Genie](https://github.com/magenta/magenta-js/tree/master/music#piano-genie) which will listen for *key presses* via USB serial.
2. Output the resulting notes via OSC. Output will be as layer than can be in the future configured for MIDI over BLE, or synthesis for audio line out.
3. Download the reference model locally, so as to not require connectivity for performances.
4. Investigate use a DAC for better line audio output.

The code will be [available in github](https://github.com/ampedAtelier/conductiveMelody).