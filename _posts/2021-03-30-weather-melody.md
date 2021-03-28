---
title: "Weather Melody"
date: 2021-03-30
tags: intangible mixd
published: false
---
**Weather Melody** is a simple Arduino sketch which fetches historical weather data using an http request API and translates it into MIDI data information.

## Weather into Music Inspiration
I am inspired by the work of the [ITP Weather Band](https://github.com/ITPNYU/weather-band) and the [weather scores of Nathalie Miebach](http://www.nathaliemiebach.com/weatherscores.html). Her work is composed of music based on weather event data, graphical and informative scores, as well as [sculptures of the scores](https://www.brainpickings.org/2011/07/12/nathalie-miebach-musical-weather-data-sculptures/). Below is an example of one of her scores based on data from [Hurricane Noel](https://en.wikipedia.org/wiki/2001_Atlantic_hurricane_season#Hurricane_Noel).

> Musical notation allows me a more nuanced way of translating information without compromising it. **~ Nathalie Miebach**

![Hurricane Noel](https://www.nathaliemiebach.com/images/score06.jpg)

## Implementation
For the implementation, I'm using the [Arduino MKR1000 WiFi]() with the [WiFi101](https://www.arduino.cc/en/Reference/WiFi101), [ArduinoHttpClient](https://www.arduino.cc/reference/en/libraries/arduinohttpclient/), and [ArduinoJson](https://arduinojson.org) libraries to fetch [wind speed data](http://weatherband.itp.io:3000/data/by-cat?macAddress=A4:CF:12:8A:C8:24&cat=windspeed) from ITP Weather Band's [Weather Server DB Web API](https://github.com/ITPNYU/Weather-Band/tree/main/database-api). The data is then mapped to MIDI notes values and sent out over USB to my laptop running Ableton Live. I chose the wind speed data point because it is the least uniform and most chaotic of the datasets.

* [ ] see [JSON library example](https://github.com/ITPNYU/Weather-Band/blob/main/get_weather_data/Arduino/get_json_from_db_parse/get_json_from_db_parse.ino)
* [ ] [Art from data TED talk](https://www.ted.com/playlists/201/art_from_data)
* [ ] [Synthesized Music Data](https://makezine.com/projects/synthesized-music-data/)
* [ ] Connect to Ableton, play, & capture as video

```C++
void setup() {
	// attempt to connect to WiFi network
	// fetch data
}
void loop() {
	// play data
}
```

## Going Further
I would love to see this has a art installation with a large LED display. This simple example uses only one data point of weather information, a fuller *score* could be achieved with additional data points. The graphical display could provide context to the data as it plays, such the event, date and time, and legend of the data points.

### BOM
| Part Name | Part Number | Cost |
|:--|:--|--:|
| *a TBD feather microcontroller* | | |
| [Adafruit AirLift FeatherWing - ESP32 WiFi Co-Processor](https://www.adafruit.com/product/4264) | 4264 | $12.95 |
| [Adafruit MIDI FeatherWing Kit](https://www.adafruit.com/product/4740) | 4740 | $6.95 |
| *a TBD standalone MIDI sound module* | | |
| [Adafruit RGB Matrix Featherwing Kit](https://www.adafruit.com/product/3036) | 3036 | $7.50 |
| *A TBD number RGB Matrix panels* | | |
