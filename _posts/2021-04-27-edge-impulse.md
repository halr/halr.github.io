---
title: "Machine Learning at Edge"
date: 2021-04-27
tags:  intangible
---
[Teachable Machine](https://teachablemachine.withgoogle.com) simplifies and streamlines gathering data and training a machine learning model for image, audio and pose based projects. It allows exporting the trained model for use with [TensorFlow](https://www.tensorflow.org), [TensorFlow.js](https://www.tensorflow.org/js), and  [TensorFlow Lite](https://www.tensorflow.org/lite/). I am more interested in running machine learning inference directly on Arduino compatible microcontrollers.

I know that [TinyML](https://tinymlbook.com) processes exists to convert a trained Tensorflow model to run a capable Arduino class device, I believe using python scripts which convert model weights from floats to integers (probably among other things). I haven't tried it, but figured it would be interesting to try. I quick online search led me to [Edge Impulse](https://www.edgeimpulse.com) though.

Edge Impulse is a company developing tools for running machine learning on edge devices. It is free for developers. You can collect data and train a model on the web in a similar fashion to Teachable Machine and deploy to supported devices such as the [Arduino Nano 33 BLE Sense](https://docs.edgeimpulse.com/docs/arduino-nano-33-ble-sense). Furthermore by installing the Edge Impulse CLI and daemon, along with the Edge Impulse firmware on the Nano you can collect data using the sensors on the Nano through the web interface.

![Collecting Data using Edge Impulse](/images/eiData.png)

Looking to try out the process, I decided to train a model to distinguish between finger snaps and hand claps. Doing so was only slightly more complicated than using Teachable Machine in that I had to select the data processing and the classifier to use. Once trained you can test the model using additional data or live through the device.

![Training using Edge Impulse](/images/eiTrain.png)

There are two options for deployment: a readily testable firmware binary and a library. The resulting library includes both your trained model and example sketches. 

![Edge Impulse deployment options](/images/eiDeploy.png)

My model didn't turn out very accurate but it can probably be fixed with more data. In [*Hands-On Machine Learning with Scikit, Keras & TensorFlow*](https://www.oreilly.com/library/view/hands-on-machine-learning/9781492032632/) Aurélien Géron talks about the importance of data. 
> The Unreasonable Effectiveness of Data: The idea that data matters more than algorithms for complex problems. Given enough data, very different ML algorithms, including fairly simple ones, perform almost identically well...

![Arduino example sketch](/images/eiArduino.png)

When in doubt add more data, and retrain!