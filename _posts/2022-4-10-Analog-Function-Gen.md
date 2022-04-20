---
layout: post
title:  "Analog Function Generator"
date:   2022-04-10 19:36:09 -0500
categories: Projects
image1: /assets/Functiongen1.jpg
image2: /assets/Functiongen2.jpg
image3: /assets/Functiongen3.jpg
image4: /assets/Functiongen0.jpg
image5: /assets/FuncRLC.jpg
image6: /assets/FuncRLC25.jpg
---

## Description
This is an attemp to create a analog function generator based on comparators and op-amps that targets a maximum frequency of 20 MHz.

The project is currently in design and simulation phase in NI Multisim. For progress till this page is updatated, please follow the link to its main repository: 
https://github.com/dexuantang/Analog-Function-Gen/tree/main/Simulations

## Block Diagram

![ Block diagram of the function generator that converts the square wave to trangular wave and then sine wave]({{ page.image4 }})


## Update
2022/4/17

The comparator used in the circuit is the TLV3501.
The comparator based oscillator is prototyped on a breadboard with a single rail 5V powersupply. ~25 Mhz max frequency is acheived. The waveform shows some distortion due to the bandwidth and propagation delay limitations.

![ Circuit on breadboard ]({{ page.image1 }})

![ Oscilloscope plot ]({{ page.image2 }})

![ Oscilloscope settings ]({{ page.image3 }})

2022/4/20

Tested the oscillator with a digital oscilloscope. The ringing in the square wave shows the step response of a second order RLC filter. This explains the noise wave seen on my analog scope on 4/17. This behavior should be the result of stray capacitance and inductance created by the component leads and the breadboard. The max frequency of this circuit built on a breadboard is also limited by this.

When designing the PCB, this ringing needs to be addressed.

Below are the plots of the second order filter step response at the max possible frequency and is shown more clearly at 7MHz.


![ Oscilloscope plot at 25MHz]({{ page.image6 }})
![ Oscilloscope plot at 7MHz]({{ page.image5 }})
