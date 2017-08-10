# Renkforce RF100 Community Firmware [![Build Status](https://travis-ci.org/probonopd/RF100-Firmware.svg?branch=community)](https://travis-ci.org/probonopd/RF100-Firmware)

Community-based Marlin firmware configured for the Conrad Electronic Renkforce RF100

![renkforce_rf100-conrad](https://user-images.githubusercontent.com/2480569/28237985-64cd60a8-694a-11e7-9f32-d54dc7c0fc24.jpg)

## What is this?

This is a recent version or Marlin 1.1.3 configured by the community for the RF100. The printer originally comes with an outdated version of Marlin. This one is much more recent, and contains the following optimizations:

- It has the Marlin 1.1.3 features and bugfixes
- It can be compiled and uploaded with the latest Arduino 1.8.x versions
- The direction ef the knob is corrected. Turning it clockwise scrolls down in the menu
- The sensitivity of the knob is improved
- You can now use the knob for bed-levelling rather than just the screws (I use the screws anyway)

## How do I use this?

Upload the firmware using __Cura__ or using the __Arduino IDE__ (selecting "Arduino/Genuino Mega or Mega 2560, ATmega2560 (Mega 2560) on /dev/ttyX" lets you upload the sketch also from the Arduino IDE. Programmer: "AVRISP mkII" - the default one), or using __avrdude__ like this:

```
sudo avrdude -v -c stk500v2 -p m2560 -P /dev/ttyUSB0 -b 115200 -U flash:w:RF100\ V1.1.cpp.hex:i -D
```

## What if I would like to go back to the official Conrad firmware?

You can backup the [original firmware](https://github.com/probonopd/RF100-Firmware/files/1214508/rf100_1.0.tar.gz) that came on your printer with

```
sudo avrdude -v -c stk500v2 -p m2560 -P /dev/ttyUSB0 -b 115200 -U flash:r:rf100_1.0.bin:i
```

Conrad Electronic also provides a compiled firmware on their product page.
