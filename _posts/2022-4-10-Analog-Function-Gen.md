---
layout: post
title:  "Analog Function Generator"
date:   2022-04-10 19:36:09 -0500
categories: Projects
image1: /assets/Functiongen1.jpg
image2: /assets/Functiongen2.jpg
image3: /assets/Functiongen3.jpg
image4: /assets/Functiongen0.jpg
---

## Description
This is an attemp to create a analog function generator based on comparators and op-amps that targets a maximum frequency of 20 MHz.

The project is currently in design and simulation phase in NI Multisim. For progress till this page is updatated, please follow the link to its main repository: 
https://github.com/dexuantang/Analog-Function-Gen/tree/main/Simulations

## Block Diagram

![ Block diagram of the function generator that converts the square wave to trangular wave and then sine wave]({{ page.image4 }})


## Update
2022/4/17

The comparator based oscillator is prototyped on a breadboard with a single rail 5V powersupply. ~25 Mhz max frequency is acheived. The waveform shows some distortion due to the bandwidth and propagation delay limitations.

![ Circuit on breadboard ]({{ page.image1 }})

![ Oscilloscope plot ]({{ page.image2 }})

![ Oscilloscope settings ]({{ page.image3 }})