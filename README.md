# Renkforce RF100 Community Firmware  [![Build Status](https://travis-ci.org/probonopd/RF100-Firmware.svg?branch=community)](https://travis-ci.org/probonopd/RF100-Firmware)

Community-based Marlin firmware configured for the Conrad Electronic Renkforce RF100

![renkforce_rf100-conrad](https://user-images.githubusercontent.com/2480569/28237985-64cd60a8-694a-11e7-9f32-d54dc7c0fc24.jpg)

The printer seems similar to the [WEISTEK](http://www.weistek.net/) Mini-Abox 3D Printer (WT560A) by Shenzhen Weistek CO., LTD.

## What is this?

This is a recent version of Marlin 1.1.6 configured by the community for the RF100. The printer originally comes with an outdated version of Marlin. This one is much more recent, and contains the following optimizations:

- It has the Marlin 1.1.6 features and bugfixes
- It can be compiled and uploaded with the latest Arduino 1.8.x versions
- The direction of the knob is corrected.
- The sensitivity of the knob is improved
- You can now use the knob for bed-levelling rather than just the screws (I use the screws anyway)
- The printable area is significantly increased to 105x110x110.

## How do I use this?

Upload the firmware using __Cura__ or using the __Arduino IDE__ (selecting "Arduino/Genuino Mega or Mega 2560, ATmega2560 (Mega 2560) on /dev/ttyX" lets you upload the sketch also from the Arduino IDE. Programmer: "AVRISP mkII" - the default one), or using __avrdude__ like this:

```
sudo avrdude -v -c stk500v2 -p m2560 -P /dev/ttyUSB0 -b 115200 -U flash:w:RF-100.ino.hex:i -D
```

## What if I would like to go back to the official Conrad firmware?

You can backup the [original firmware](https://github.com/probonopd/RF100-Firmware/files/1214508/rf100_1.0.tar.gz) that came on your printer with

```
sudo avrdude -v -c stk500v2 -p m2560 -P /dev/ttyUSB0 -b 115200 -U flash:r:rf100_1.0.bin:i
```

Conrad Electronic also provides a compiled firmware on their product page.

## Hardware information

### Mainboard

HICTOP 3D Printer Control Board MPX.3, similar to an Arduino Mega with an integrated RAMPS 1.4, https://github.com/MarlinFirmware/Marlin/issues/2906

## Hardware upgrades

### Functional upgrades

* Printout Debug Information for HotEnd (Thermistor) on M109
* Printout last reading of Thermistor before System halts on "MAX_TEMP_REACHED" (Nice for debugging the Thermistor)
* Added "Load Filmament // Unload Filmament // Feed Filmament" to Prepare-Menu
* The standard print bed does not make full use of the available build space, there is at least 3 cm more available in the Y dimension. This makes quite a big difference! To use the original print bed without modification, width is changed to 110mm, depth to 110mm, height to 110mm.
* Automatic bed leveling. Possibly a sensor like the LJC18A3 might work (to be investigated).
* Wireless printing https://github.com/probonopd/WirelessPrinting

### Hardware bugfixes

* Make the fan double as a part cooling fan. Different solutions are available on Thingiverse. Possibly design something using a blower fan (like https://www.thingiverse.com/thing:1652852/)?
* Clip to prevent the ribbon cable that goes to the extruder from breaking. [Available on Thingiverse](https://www.thingiverse.com/thing:2455984). Highly recommended to be installed as the first thing on this printer, since the cable has a tendency to break. Apparently newer versions of the machines no longer use a flat ribbon cable.
