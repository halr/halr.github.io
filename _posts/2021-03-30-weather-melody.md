---
title: "Weather Melody"
date: 2021-03-30
tags: intangible mixd
---
**Weather Melody** is an Arduino sketch which fetches historical weather data using an http request API and translates it into MIDI messages.

## Weather to Music Inspiration
> Musical notation allows me a more nuanced way of translating information without compromising it. **~ Nathalie Miebach**

I am inspired by the work of the [ITP Weather Band](https://github.com/ITPNYU/weather-band) and particularly the [weather scores of Nathalie Miebach](http://www.nathaliemiebach.com/weatherscores.html). As she describes in a short Ted Talk: [Art made of Storms](https://www.ted.com/talks/nathalie_miebach_art_made_of_storms) (2011), she gathers weather event data, creates graphical and informative musical scores from the data, and finally translates the [scores into sculptures](https://www.brainpickings.org/2011/07/12/nathalie-miebach-musical-weather-data-sculptures/). Below is an example of one of her scores based on data from [Hurricane Noel](https://en.wikipedia.org/wiki/2001_Atlantic_hurricane_season#Hurricane_Noel).

![Hurricane Noel](https://www.nathaliemiebach.com/images/score06.jpg)

## Implementation
For the implementation, I'm using the [Arduino MKR1000 WiFi]() with the [WiFi101](https://www.arduino.cc/en/Reference/WiFi101), [ArduinoHttpClient](https://www.arduino.cc/reference/en/libraries/arduinohttpclient/), and [MIDIUSB](https://github.com/arduino-libraries/MIDIUSB) libraries to fetch [weather data by id](http://weatherband.itp.io:3000/data/id/102) from ITP Weather Band's [Weather Server DB Web API](https://github.com/ITPNYU/Weather-Band/tree/main/database-api). Temperature and humidity values are then mapped to MIDI note and velocity values respectively and sent out as MIDI messages over USB to my laptop running Ableton Live. The code will be github soon.

I had some issues with fetching data consistently using the Arduino MKR1000 WiFi which cleared up once I [updated the WiFi 101 firmware](https://www.arduino.cc/en/Tutorial/FirmwareUpdater).

```C++
void loop() {
  // ...
  // not shown: fetching the weather data by id, etc.
  // ...
  int temperature = parseJsonForValue(weatherRsp, "temperature");
  int humidity = parseJsonForValue(weatherRsp, "humidity");
	      
  int note = constrain(temperature, 0, 127);
  int velocity = constrain(humidity, 0, 127);
  // play data
  sendNoteOn(0,note,velocity);
  lastNote = note;	// so we can release the note later 
}

float parseJsonForValue(String json, String key) {
  // parse the response looking for key:
  int labelStart = json.indexOf(key);
  int dataStart = json.indexOf(" ", labelStart);
  int dataEnd = json.indexOf(",", dataStart);
  String dataStr = json.substring(dataStart + 1, dataEnd);
  Serial.println(dataStr);
  float returnValue = dataStr.toFloat();
  returnValue+=0.5;	// to handle rounding
  return returnValue;
}

void sendNoteOn(byte channel, byte pitch, byte velocity) {
  midiEventPacket_t midiMsg = {0x09, 0x90 | channel, pitch, velocity};
  MidiUSB.sendMIDI(midiMsg);
}

void sendNoteOff(byte channel, byte pitch, byte velocity) {
  midiEventPacket_t midiMsg = {0x08, 0x80 | channel, pitch, velocity};
  MidiUSB.sendMIDI(midiMsg);
}
```

## Next Steps
Currently, I am only using temperature and humidity, but air pressure is also an interesting reading. I would like to map pressure to, possibly, a MIDI control change message to alter the note timbre.

## Going Further
I would love to see this has an art installation with a large LED display. This simple example uses only a couple of data points of weather information, a fuller *score* could be achieved with additional data points. The graphical display could provide context to the data as it plays, such the event, date and time, and legend of the data points.

It would be interesting to analyze the complete dataset either in the manner of Nathalie Miebach or using a python Jupyter notebook.

### BOM

| Part Name | Part Number | Cost |
|-----------|------------:|-----:|
| *a TBD feather microcontroller* | | |
| [Adafruit AirLift FeatherWing - ESP32 WiFi Co-Processor](https://www.adafruit.com/product/4264) | 4264 | $12.95 |
| [Adafruit MIDI FeatherWing Kit](https://www.adafruit.com/product/4740) | 4740 | $6.95 |
| *a TBD standalone MIDI sound module* | | |
| [Adafruit RGB Matrix Featherwing Kit](https://www.adafruit.com/product/3036) | 3036 | $7.50 |
| *A TBD number RGB Matrix panels* | | |
