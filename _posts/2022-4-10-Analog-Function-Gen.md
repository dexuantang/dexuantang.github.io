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
image7: /assets/functiongenin.png
image8: /assets/FUNCI.jpg
image9: /assets/FUNCI2.jpg
image10: /assets/candidate.png
---

## Description
This is an attemp to create a analog function generator based on comparators and op-amps that targets a maximum frequency of 20 MHz.

The project is currently in design and simulation phase in NI Multisim. For progress till this page is updatated, please follow the link to its [main repository](https://github.com/dexuantang/Analog-Function-Gen/tree/main/Simulations).

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

2022/5/16

High speed op-amp (AD8062ARMZ) arrived for the integrator stage prototype.

![Current schematics]({{ page.image7 }})

Tested the circuit on a breadboard up to 5MHz. The +-2.75V supply was generated with two LEDs in series that regulate a 5.5V input. Proper voltage regulators will be used in the final design, The integrator will use +-4V supply to prevent saturation.

![Breadboard circuit]({{ page.image8 }})
![scope display]({{ page.image9 }})

Because the frequency of the waveform is controlled by the threshold of the comparator and the RC circuit has a small time constant, lower frequency cannot be generated with the current configuration. A range switch or a corse adjustment will be designed to alter the time constant of the RC circuit.

#### 2022/5/21 Signal stage design candidate

Now the square wave is controlled by the triangular wave. The triangular wave is fed into the comparator in a Schmitt trigger configuration. This will make sure that the amplitude of the triangular wave does not change too much. A range switch and a fine adjustment potentiometer for frequency is added. The square wave and triangular wave stages were tested on bread board and produced good result.

The sine wave stage is designed. It uses a 8-diode shaper circuit which exploits the non-linear voltage transfer curve of diodes. The schematic and simulation is available through the repository for this project. This design will likely be very similar to the final design.

![design candidate with all three stages]({{ page.image10 }})

