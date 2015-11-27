# Cheap Hue
The goal of this project is to create an actual usable clone of the Phillips Hue lights.

## Reason
If you search online for a wifi controlled RGB LED you'll find hunderds of simular projects, but I will try to approach it differently.
My goal is not an RGB led that dangles with a few wires on a Raspberry Pi or an Arduino because this is not something you want to use in the living room. But if we build a clone it's important that you can install it as easy as the actual Hue lights, just by screwing it into your standard E27 light fitting.

Another goal is that it should at least be 50% cheaper (max €30) as the actual Hue lights.

## Difference
One of the biggest differences is that we will not use a bridge to connect to the wifi.
Our bulbs will connect directly to wifi network. The disadvantages of this:

* potential connection problems when the bulb is to far removed from your wifi access point
* we have to configure the wifi SSID and password into our bulb source code which sucks (something like [this firmware](http://www.instructables.com/id/ESP8266-based-web-configurable-wifi-general-purpos-1/) could solve this)

## Software
The software part of this project will be written in [LUA](https://en.wikipedia.org/wiki/Lua_(programming_language)) in combination with [NodeMCU firmware](https://github.com/nodemcu/nodemcu-firmware).

I've chosen this firmware because it's activly developed and has a large user base which should result in a stable and "bug free" base for my project.

_Another option is that I will write this in C which will obviously be a lot harder but then I could use this as my final project of my CS50 course._

## Hardware
This is a list of hardware I will try to use to create an initial prototype of this project. This list can change over time depending on the results a get with certain components.

The Hue led bulbs are 10W so I will use a few leds to mimic this.

* [E27 Light bulb casing](http://www.dx.com/p/e27-3w-white-light-led-bulb-silver-white-110-240v-257622#.VjIpjq7nsQ8) [current] _€3.80_
* [E27 Light bulb casing](http://www.dx.com/p/e27-5w-5-led-aluminum-bulb-accessories-shell-silver-81765#.VjIpUK7nsQ8) [optional] _€3.78_
* [ESP8266](http://www.dx.com/p/esp-07-esp8266-uart-serial-to-wi-fi-wireless-module-with-built-in-antenna-for-arduino-raspberry-pi-375400#.VjItSa7nsQ8) _€4.38_
* [Power supply](http://www.dx.com/p/7w-led-constant-current-source-power-supply-driver-100-240v-141983#.VjIpAa7nsQ8) _€4.52_
* [3x 3w RGB LED](http://www.dx.com/p/3w-4-pin-rgb-led-light-bulb-223579#.VjIts67nsQ8) [current] _3 x €1.61 = €4.83_
* [2x 5-wat RGB LED](http://www.dx.com/p/5-watt-70-lumen-rgb-led-emitter-20999#.VjItp67nsQ8) [optional] _2x€4.09 = €8.18_

Current total: __€17.53__

_We could potentially save some extra bucks if we order some parts on BangGood._

## API
The bulb should have a API that closely matches the Hue light API.

|         |                       Get light state |
|:--------|--------------------------------------:|
| Address | `http://<bulb ip address>/api/light/` |
| Body    |                        `{"on":false}` |
| Method  |                                   GET |

|         |                         Update light state |
|:--------|-------------------------------------------:|
| Address | `http://<bulb ip address>/api/light/state` |
| Body    |                              `{"on":true}` |
| Method  |                                        PUT |

|         |                                Update light color |
|:--------|--------------------------------------------------:|
| Address |        `http://<bulb ip address>/api/light/state` |
| Body    | `{"on":true, "sat":254, "bri";254, "hue": 10000}` |
| Method  |                                               PUT |

## Automatic firmware updates
It would be very cool and handy if the light could automatically detect if there are online updates and if so install them.

For more information search for OTA or [FOTA](https://harizanov.com/2015/06/firmware-over-the-air-fota-for-esp8266-soc/).

## Inside Hue
Some teardown post that can give some insides about the Hue light

* [Phillips Hue light teardown](https://plus.google.com/photos/107696725527584609973/albums/5806291983792940817)
* [Phillips HUE and RGB LED Strip](https://www.youtube.com/watch?v=Mg_Iw4yzilI)

## Contributing

1. Fork it!
2. Create your feature branch: git checkout -b my-new-feature
3. Commit your changes: git commit -m 'Add some feature'
4. Push to the branch: git push origin my-new-feature
5. Submit a pull request :D

## License
[MIT License](http://opensource.org/licenses/MIT)

I'm not responsible (it is provided as-is; no warranty, liability, etc.)
