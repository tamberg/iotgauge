# IoT Gauge with Adafruit Feather HUZZAH

Based on http://www.instructables.com/id/IoT-Gauge-with-Arduino-Yaler-IFTTT by [tamberg.org](http://www.tamberg.org/), licensed [CC BY-SA](https://creativecommons.org/licenses/by-sa/2.5/)

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

## Part 0: Getting started

How to set up the Arduino development environment and run your first program on the Adafruit Feather HUZZAH.

### Install the Arduino IDE
Install the [Arduino.cc IDE](https://www.arduino.cc/en/Main/Software) v1.6.4 or newer, if you don't have it yet.

### Install the CP2104 USB driver
Install the [USB driver](https://www.silabs.com/products/mcu/pages/usbtouartbridgevcpdrivers.aspx) for Adafruit Feather HUZZAH / CP2104.

### Add the ESP8266 board to the Arduino IDE
Follow [this Adafruit tutorial](https://learn.adafruit.com/adafruit-feather-huzzah-esp8266/using-arduino-ide#install-the-esp8266-board-package) to add the Adafruit Feather HUZZAH / ESP8266 board package.

(Or add `http://arduino.esp8266.com/stable/package_esp8266com_index.json` to _Additional Board Manager URLs_ then go tto _Tools > Board MAnager_ and search for _ESP_.)

Quit and reopen the Arduino IDE.

### Select the ESP8266 and the current USB port

In the Arduino IDE, select _Tools > Board > Adafruit HUZZAH ESP8266_.

Then select _Tools > CPU Frequency > 80 MHz_.

Then select _Port > ..._ (e.g. _COM3_ on Windows or _/dev/tty.usb-..._ on Mac OSX)

(Or follow [this Adafruit tutorial](https://learn.adafruit.com/adafruit-feather-huzzah-esp8266/using-arduino-ide#setup-esp8266-support) for detailed instructions.)

### Upload the Blink example to the Adafruit Feather HUZZAH

In the Arduino IDE, open _File > Examples > Basic > Blink_ then click the upload icon. An LED should now blink.

(Or, for detailed instructions see [this Adafruit tutorial](https://learn.adafruit.com/adafruit-feather-huzzah-esp8266/using-arduino-ide#blink-test).)

## Part 1: Laser-cutting and assembling the IoT Gauge

### Use a laser to cut the design from 4mm plywood

The IoT Gauge physical [design files](https://www.thingiverse.com/thing:453788/#files) are available on Thingiverse.

<img src="http://cdn.instructables.com/FK5/FGHY/ICBS2RIP/FK5FGHYICBS2RIP.MEDIUM.jpg" width="512" />

### Assemble the IoT Gauge

Stick the base plate into the big face plate, then into the small one.

Then, add the servo. Make sure the servo axle is centered.

Then, add the the disks and finally the clock hand.

<img src="https://c1.staticflickr.com/9/8627/28505434551_1fee6161e4_z.jpg" width="512" />

Make sure the nice side of the wood faces to the front.

<img src="https://c2.staticflickr.com/8/7192/27666972152_4c62c96afc_z.jpg" width="512" />

(Note that you don't have to write anything on the disks yet.)

### Connect the jumper wires

* Black (or brown) servo wire to GND
* Red servo wire to USB
* Yellow (or orange) servo wire to pin 2

<img src="https://c1.staticflickr.com/9/8653/28482309991_4ee6f6ed70.jpg">

### Testing the servo

In the Arduino IDE, try _File > Examples > Servo (esp8266) > Sweep_.

### Mount the breadboard to the base plate

Use zip wire or just stick the breadboard to the base plate.

<img src="https://c2.staticflickr.com/8/7441/27666978202_9532f03635_z.jpg" width="512" />

## Part 2: Uploading the IoT Gauge Web service code

Controlling the IoT Gauge is quite simple. A Web service (or REST API) is listening for incoming requests and setting the servo position accordingly. To give IFTTT access to the IoT Gauge, our Arduino REST API needs to be accessible from the Web. Experts could add an exception to their firewall or router. But as this can be quite a hassle, we'll use the Yaler relay service.

### Install the ESP8266 Yaler library

Sign up for a free trial account at [Yaler.net](https://yaler.net/) to get a RELAY_DOMAIN (required below).

Download the [YalerESP8266WiFiServer.zip](https://bitbucket.org/yaler/yalercontrib/downloads/YalerESP8266WiFiServer.zip) library

On Mac OS X, extract the ZIP to `~/Documents/Arduino/libraries/YalerESP8266WiFiServer`

On Windows, extract the ZIP to `C:\Users\USER_NAME\Documents\Arduino\Libraries\YalerESP8266WiFiServer`

Then, close and reopen the Arduino IDE to load the library.

### Get the IoT Gauge Web service source code

Right click and download [IoTGaugeWebService.ino](https://bitbucket.org/tamberg/iotworkshop/raw/tip/ESP8266/IoTGaugeWebService/IoTGaugeWebService.ino) and open it in the Arduino IDE.

(Or copy & paste the source code into a new Arduino sketch.)

### Set RELAY_DOMAIN, LOCAL_NETWORK_SSID and _PASSWORD

Set LOCAL_NETWORK_SSID and LOCAL_NETWORK_PASSWORD according to the local Wi-Fi network.

(Note that LOCAL_NETWORK_* has to be adapted whenever the IoT Gauge is moved to another local network.)

Then replace RELAY_DOMAIN with your relay domain from https://yaler.net/account (the string starting with gsiot-...)

### Upload the IoT Gauge Web service source code

Click the upload icon to store the code to the Adafruit Feather HUZZAH.

### Open the Arduino IDE serial monitor

Make sure the _baud_ rate is set to _115200_, not _9600_ as in the picture.

<img src="https://c1.staticflickr.com/9/8724/28281929600_fbd9081a82_z.jpg" />

## Part 3: Testing the IoT Gauge Web service with Curl

### Make sure the Curl tool is installed

Open a Terminal or command line on your computer.

Type `$ curl --version` to make sure Curl is installed.

If necessary, download and install Curl from https://curl.haxx.se/download.html

### Set the servo position

Type `$ curl -vX PUT http://RELAY_DOMAIN.try.yaler.io/servo?pos=3` to set the servo to position 3 (center).

Make sure to replace RELAY_DOMAIN with the same relay domain you used above. The output should say _200 OK_.

Try any position between 1 and 5. Make sure the servo moved to the desired position (adjust the hand if necessary).

## Part 4: Connecting the IoT Gauge to the IFTTT Maker channel

### Creating a new IFTTT recipe (or skip to add an existing recipe)

IFTTT lets you create recipes connecting a trigger to an action.

* Visit https://ifttt.com/myrecipes/personal/new (sign up if you haven't yet)
* To choose a trigger channel, search for e.g. "Android Device" or "iOS Location" and select the channel icon
* Then choose a trigger, e.g. Connects to a specific WiFi network (for Android)
* Enter a network name or location
* When choosing action channel, search for the Maker channel and select it
* Then select the action Make a web request
* Enter the URL `http://RELAY_DOMAIN.try.yaler.io/servo?pos=3` (Replace RELAY_DOMAIN as before)
* For the Method select _PUT_
* For the Content Type select _application/x-www-form-urlencoded_
* The Body can be left empty

<img src="http://cdn.instructables.com/FFB/CSXJ/ICEMSWZM/FFBCSXJICEMSWZM.MEDIUM.jpg" width="512" />

### Adding an existing IFTTT recipe

IFTTT allows users to publish recipes. Here are two recipes to control your IoT Gauge:

* Open the "IoT Gauge position from Android WiFi location" <a href="https://ifttt.com/recipes/309367-iot-gauge-position-from-wifi-location">recipe here</a>
* Or the "IoT Gauge position from iOS location" <a href="https://ifttt.com/recipes/309375-iot-gauge-position-from-ios-location">recipe here</a>
* To add an instance of the recipe to your recipes click the _Add_ button
* Enter a WiFi network name or location (or whatever the recipe asks for)
* Replace RELAY_DOMAIN in the URL with the relay domain you used before
* Adapt the pos parameter in the URL from 1 to 5 to match your location
* Add another instance of the recipe for each location

<img src="http://cdn.instructables.com/FXL/RNFV/ICEMY3CB/FXLRNFVICEMY3CB.MEDIUM.jpg" width="253" />  <img src="http://cdn.instructables.com/FRR/RC1Y/ICEMY39P/FRRRC1YICEMY39P.MEDIUM.jpg" width="253" />

## Part 5: Creating a IFTTT Do button for the IoT Gauge (optional)

IFTTT also provides Do apps for iOS and Android. The app allows you to manually trigger actions. This can be great for testing your other IFTTT recipes. Unlike normal IFTTT recipes, the Do app recipes cannot be shared or made public. So you'll have to create them from scratch.

### Creating a new IFTTT Do button

* Get the Do Button Android or iPhone app at https://ifttt.com/products/do/button
* Work through the rather annoying but mandatory (?) intro screens
* Use the small icon on the lower right to bring up the list of recipes
* Tap the + sign, then tap Channels and search for the Maker channel
* Then select the action Make a web request
* Enter the URL http://RELAY_DOMAIN.try.yaler.io/mailbox/pos/3
(Replace RELAY_DOMAIN as before)
* For the Method select _POST_
* For the Content Type select _application/x-www-form-urlencoded_
* The Body can be left empty
* Tap Add to create the button
* Once created, the recipe can be edited online at https://ifttt.com/myrecipes/do

<img src="http://cdn.instructables.com/FZ2/D7OS/ICEMT9V9/FZ2D7OSICEMT9V9.MEDIUM.jpg" width="512" />
