# IoT Gauge with Adafruit Feather HUZZAH

Based on http://www.instructables.com/id/IoT-Gauge-with-Arduino-Yaler-IFTTT/

<img src="http://cdn.instructables.com/FMO/J4IT/ICEMXRME/FMOJ4ITICEMXRME.MEDIUM.jpg"/>

How to build a Web-enabled IoT Gauge with a REST API, and connect it to the [IFTTT.com](https://ifttt.com/) mash-up platform, via the [Yaler.net](https://yaler.net/) relay service. Not sure what that means? No worries. Just follow the simple steps below.

Inspired by [WhereDial](http://blog.mapme.at/wheredial/), a DIY Internet of Things classic, the IoT Gauge shows the current location of its owner. A bit like the Weasley Clock in Harry Potter.

## Material

* https://www.adafruit.com/products/155 (Servo)
* http://www.play-zone.ch/de/adafruit-feather-huzzah-with-esp8266-wifi.html
* http://www.play-zone.ch/de/hispeed-usb-kabel-2-0-a-micro-5-pin-150cm-schwarz.html
* http://www.play-zone.ch/de/elektronik-kit-zubehoer/breadboards/lochraster-steckplatine-breadboard-170.html
* http://www.play-zone.ch/de/jumperkabel-10-stk-m-m-verbindungskabel-10cm.html (3 jumper wires)
* http://www.play-zone.ch/de/netzteil-ac-dc-adapter-5v-dc-1000ma-usb.html

## Tools

* Laser-cutter
* Hot-glue or wood glue
* Android or iOS smartphone

## Downloads

All downloads are listed here for convenience, we will use them later on

* IoT Gauge physical [design files](https://www.thingiverse.com/thing:453788/#files) on Thingiverse
* [USB driver](https://www.silabs.com/products/mcu/pages/usbtouartbridgevcpdrivers.aspx) for Adafruit Feather HUZZAH / CP2104
* [Arduino IDE](https://www.arduino.cc/en/Main/Software) from Arduino.cc, if you don't have it yet
* [YalerESP8266WiFiServer.zip](https://bitbucket.org/yaler/yalercontrib/downloads/YalerESP8266WiFiServer.zip) library for remote access
* [IoTGaugeWebService.ino](https://bitbucket.org/tamberg/iotworkshop/raw/tip/ESP8266/IoTGaugeWebService/IoTGaugeWebService.ino) source code for Adafruit Feather HUZZAH / ESP8266

## Installing the Arduino IDE
Install [Arduino IDE](https://www.arduino.cc/en/Main/Software) from Arduino.cc, if you don't have it yet

## Installing the CP2104 USB driver
Install the [USB driver](https://www.silabs.com/products/mcu/pages/usbtouartbridgevcpdrivers.aspx) for Adafruit Feather HUZZAH / CP2104

## Adding the ESP8266 board to the Arduino IDE
Follow [this Adafruit tutorial](https://learn.adafruit.com/adafruit-feather-huzzah-esp8266/using-arduino-ide#install-the-esp8266-board-package) to add the Adafruit Feather HUZZAH / ESP8266 board package

## 
