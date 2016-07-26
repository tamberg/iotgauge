# IoT Gauge with Adafruit Feather HUZZAH

Based on http://www.instructables.com/id/IoT-Gauge-with-Arduino-Yaler-IFTTT by [tamberg.org](http://www.tamberg.org/), licensed [CC BY-SA](https://creativecommons.org/licenses/by-sa/2.5/).

<img src="http://cdn.instructables.com/FMO/J4IT/ICEMXRME/FMOJ4ITICEMXRME.MEDIUM.jpg"/>

How to build a Web-enabled IoT Gauge with a REST API, and connect it to the [IFTTT.com](https://ifttt.com/) mash-up platform, via the [Yaler.net](https://yaler.net/) relay service. Not sure what that means? No worries. Just follow the simple steps below.

Inspired by [WhereDial](http://blog.mapme.at/wheredial/), a DIY Internet of Things classic, the IoT Gauge shows the current location of its owner. A bit like the Weasley Clock in Harry Potter.

### Material

* 1 Servo ([Adafruit](https://www.adafruit.com/products/155))
* 1 Adafruit Feather HUZZAH ([Adafruit](https://www.adafruit.com/products/2821) or [Playzone](http://www.play-zone.ch/de/adafruit-feather-huzzah-with-esp8266-wifi.html))
* 1 mini bread board ([Adafruit](https://www.adafruit.com/products/65) or [Playzone](http://www.play-zone.ch/de/elektronik-kit-zubehoer/breadboards/lochraster-steckplatine-breadboard-170.html))
* 3 M/M jumper wires ([Adafruit](https://www.adafruit.com/products/1956) or [Playzone](http://www.play-zone.ch/de/jumperkabel-10-stk-m-m-verbindungskabel-10cm.html))
* 1 USB cable A/MicroB ([Adafruit](https://www.adafruit.com/products/592) or [Playzone](http://www.play-zone.ch/de/hispeed-usb-kabel-2-0-a-micro-5-pin-150cm-schwarz.html))
* 1 USB adapter ([Adafruit](https://www.adafruit.com/products/501) or [Playzone](http://www.play-zone.ch/de/netzteil-ac-dc-adapter-5v-dc-1000ma-usb.html))
* 1 A3 sheet of 4mm plywood
* 2 small zip ties

### Tools

* Laser-cutter
* Hot-glue or wood glue
* Android or iOS smartphone

### Downloads

All downloads are listed here for convenience, we will use them later on.

* IoT Gauge physical [design files](https://www.thingiverse.com/thing:453788/#files) on Thingiverse
* [USB driver](https://www.silabs.com/products/mcu/pages/usbtouartbridgevcpdrivers.aspx) for Adafruit Feather HUZZAH / CP2104
* [Arduino IDE](https://www.arduino.cc/en/Main/Software) from Arduino.cc, if you don't have it yet
* [YalerESP8266WiFiServer.zip](https://bitbucket.org/yaler/yalercontrib/downloads/YalerESP8266WiFiServer.zip) library for remote access
* [IoTGaugeWebService.ino](https://bitbucket.org/tamberg/iotworkshop/raw/tip/ESP8266/IoTGaugeWebService/IoTGaugeWebService.ino) source code for Adafruit Feather HUZZAH / ESP8266

## Step 0: Getting started

How to set up the Arduino development environment and run your first program on the Adafruit Feather HUZZAH.

### Install the Arduino IDE
Install the [Arduino.cc IDE](https://www.arduino.cc/en/Main/Software) v1.6.4 or newer, if you don't have it yet.

### Install the CP2104 USB driver
Install the [USB driver](https://www.silabs.com/products/mcu/pages/usbtouartbridgevcpdrivers.aspx) for Adafruit Feather HUZZAH / CP2104.

### Add the ESP8266 board to the Arduino IDE
Follow [this Adafruit tutorial](https://learn.adafruit.com/adafruit-feather-huzzah-esp8266/using-arduino-ide#install-the-esp8266-board-package) to add the Adafruit Feather HUZZAH / ESP8266 board package.

### Select the ESP8266 and USB port

Follow [this Adafruit tutorial](https://learn.adafruit.com/adafruit-feather-huzzah-esp8266/using-arduino-ide#setup-esp8266-support).

### Upload the Blink example to the Adafruit Feather HUZZAH

In the Arduino IDE, open _File > Examples > Basic > Blink_ then click the upload icon. An LED should now blink.

For details see [this Adafruit tutorial](https://learn.adafruit.com/adafruit-feather-huzzah-esp8266/using-arduino-ide#blink-test).

## Step 1: Laser-cutting and assembling the IoT Gauge

### Use a laser to cut the design from 4mm plywood
The IoT Gauge physical [design files](https://www.thingiverse.com/thing:453788/#files) are available on Thingiverse.

<img src="http://cdn.instructables.com/FK5/FGHY/ICBS2RIP/FK5FGHYICBS2RIP.MEDIUM.jpg" width="512" />

### Assemble the IoT Gauge

<img src="https://c2.staticflickr.com/8/7441/27666978202_9532f03635_z.jpg" width="512" />

<img src="https://c2.staticflickr.com/8/7192/27666972152_4c62c96afc_z.jpg" width="512" />

### Connect the jumper wires

* Black servo wire to GND
* Red servo wire to USB
* Yellow servo wire to pin 2

<img src="https://c1.staticflickr.com/9/8653/28482309991_4ee6f6ed70.jpg">

## Step 2: Uploading the IoT Gauge Web service Arduino code

###

## Step 3: Testing the Arduino Web service with Curl

###

## Step 4: Connecting the IoT Gauge to the IFTTT Maker channel

###

## Step 5: Creating a IFTTT Do button for the IoT Gauge

###
