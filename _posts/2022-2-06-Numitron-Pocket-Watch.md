---
layout: post
title:  "Numitron Pocket Watch"
date:   2022-02-06 10:27:09 -0500
categories: Projects
image1: /assets/watch1.jpg
image2: /assets/watch2.jpg
image3: /schematics.webp
---
![Image of the watch]({{ page.image1 }})

Link to video: [YouTube](https://youtu.be/2LIIfYBfglk)

## descriptions
    I started this project in October of 2019. Numitron tubes are incandescent 7 segments display tubes used before LED technology was available. This is also my first complete PCB design. The electronics part of my current version consists of two IV-9 numitron tubes, an Adafruit ItsyBitsy 32u4 3v microcontroller development board with an RTC chip, and seven PNP transistors for switching the segments with two NPN transistors for switching between the displays. The device is powered by a 400 mAh lithium battery which can be charged by an external battery management module. 

    The current time is provided to the microcontroller by the RTC chip via the I2C bus. The microcontroller will then switch on the corresponding display segments using the seven PNP transistors as high side switches according to the digits of the current time and alternate between the digit for the two displays at a high frequency invisible to human eye. At the same time, the two NPN transistors act as low side switches that close the circuit between the two ground pins of the numitron displays and the ground of the circuit at the same frequency.

    Each segment pin of the displays has a diode on it to prevent reverse current turning on unwanted segments.

    A reed switch is used to turn on the display when a magnet is removed to conserve power. (In hindsight a hall effect sensor is probably a better idea since it includes no moving parts.)

    I drew the schematics and PCB using EasyEDA and ordered the PCB from a prototyping vendor.

    The firmware was written with Arduino IDE, I used the existing library “SevSeg” for easier handling of multiplexing.

    ![Another image of the watch]({{ page.image2 }})
    ![schematics]({{ page.image3 }})


