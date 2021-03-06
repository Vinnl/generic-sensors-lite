# GENERIC-SENSORS-LITE #

[![GitHub forks](https://img.shields.io/github/forks/rzr/generic-sensors-lite.svg?style=social&label=Fork&maxAge=2592000)](https://GitHub.com/rzr/generic-sensors-lite/network/)
[![license](https://img.shields.io/badge/license-Apache-2.0.svg)](LICENSE)
[![NPM](https://img.shields.io/npm/v/generic-sensors-lite.svg)](https://www.npmjs.com/package/generic-sensors-lite)
[![Build Status](https://api.travis-ci.org/rzr/generic-sensors-lite.svg?branch=master)](https://travis-ci.org/rzr/generic-sensors-lite)
[![dependencies Status](https://david-dm.org/rzr/generic-sensors-lite/status.svg)](https://david-dm.org/rzr/generic-sensors-lite)
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Frzr%2Fgeneric-sensors-lite.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2Frzr%2Fgeneric-sensors-lite?ref=badge_shield)

[![NPM](https://nodei.co/npm/generic-sensors-lite.png)](https://npmjs.org/package/generic-sensors-lite)


## INTRODUCTION: ##

Lightweight implementation of W3C spec, targeting constrained devices.

Several JavaScript runtimes are supported (node.js, IoT.js using JerryScript)

[![Presentation](https://image.slidesharecdn.com/webthing-iotjs-20181022rzr-181027220201/95/webthingiotjs20181022rzr-34-638.jpg)](https://www.slideshare.net/slideshow/embed_code/key/BGdKOn9HHRF4Oa#webthing-iotjs# "WebThingIotJs")


## USAGE: ##

Following sensors can be plugged on pins of your favorite single board computer:

* BH1650: for measuring illuminance  (i2c=0x23)
* BMPx80: for measuring temperature, or any compatible sensor (ie: BMP180, i2c=0x77)


#### SETUP: ####

Privileged access to hardware resources is also required too (setup or use sudo).

For instance on Raspbian:

``` 
sudo raspi-config # Enable I2C
ls -l /dev/i2c* || sudo reboot
sudo apt-get install i2c-tools
/usr/sbin/i2cdetect -y 1

     0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:          -- -- -- -- -- -- -- -- -- -- -- -- -- 
10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
20: -- -- -- 23 -- -- -- -- -- -- -- -- -- -- -- -- 
30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
50: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
60: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
70: -- -- -- -- -- -- -- 77
```

#### USING NODE.JS: ####

```
git clone --recursive https://github.com/rzr/generic-sensors-lite
cd generic-sensors-lite
npm install
npm test
(...)
log: temperature: 28.1
log: ambientlight: 51
log: temperature: 28.1
log: temperature: 28.1
log: ambientlight: 51
(...)

```


#### USING IOT.JS ####

For constrained environments:

```
make runtime=iotjs run
# (...)
# iotjs example/index.js 
# log: temperature: 31.8
# log: ambientlight: 16.666666666666668
# (...)
```

Note: It has been verified on GNU/Linux not TizenRT yet (TODO).


### DEMO: ###

[![web-of-things-agriculture-20180712rzr.webm](https://media.giphy.com/media/tKyrtKMc77iV9QUCrP/giphy.gif)](https://player.vimeo.com/video/279677314#web-of-things-agriculture-20180712rzr.webm "Video Demo")

An extra example is provided to show integration in Mozilla's Thing project.
Sensors are powered by webthing-iotjs and monitored on dashboard as progressive web app (PWA).

Usage:

```sh
make runtime=iotjs run
make -C example/webthing runtime=iotjs run
# (...)
# log: AmbientLight: AmbientLight: change: 28.333333333333336
# log: Temperature: Temperature: change: 33
# (...)
```

Respectively node could be supported too,
just adapt to webthing-node API instead of webthing-iotjs (TODO):

```sh
make -C example/webthing runtime=node run
# (...)
```


## RESOURCES: ##

* https://www.npmjs.com/package/generic-sensors-lite
* https://github.com/rzr/generic-sensors-lite
* https://w3c.github.io/sensors/
* https://github.com/rzr/mozilla-iot-generic-sensors-adapter
* https://s-opensource.org/2018/04/25/mozilla-iot-generic-sensors/
* https://github.com/miroRucka/bh1750/pull/17
* https://github.com/dbridges/bmp085-sensor/pull/7
* https://github.com/samsung/iotjs/wiki
* https://github.com/samsung/iotjs
* http://www.iotjs.net/
* http://jerryscript.net/
* https://github.com/rzr/webthing-iotjs/wiki/IotJs
* https://github.com/rzr/webthing-iotjs/wiki/Sensor
* https://social.samsunginter.net/@rzr/100969945665369600


## LICENSE: ##

[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Frzr%2Fgeneric-sensors-lite.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Frzr%2Fgeneric-sensors-lite?ref=badge_large)
