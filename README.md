Electron Power Management
---
[Place to host the experimental power supply design files for the Electron]

> To put it simply, the challenge in designing the power supply unit for the Electron is _supply and demand_. 

A cellular module is a power hungry device. Unlike WiFi, a GSM module requires a higher burst of power during transmission. These power/current spikes can go as high as 2Amps. This clearly exceeds USB's limit of 500mA in most cases. When developing on the Electron connected to a computer, care must be taken not to exceed the USB's limit while maintaining uninterrupted power to the cellular module. Most portable devices overcome this by having a battery connected at all times, like mobile phones. For a device like the Electron, it becomes essential to have the flexibility to power it either via the USB, battery or both.

The USB powered GSM modems currently available in the market use a switch-mode DC regulator with a high capacity bulk capacitor at the output. This capacitor stores enough energy to power the GSM module during its peak power requirements. At the same time, the regulator makes sure not to exceed the 500mA limit of draw current from a USB port. Most of the USB ports on today's computers are capable of sourcing 1Amp of continuous current. This allows for the use of a smaller bulk capacitor, but you still need to use one.

Things get a little interesting when you consider that 2G and 3G power requirements are completely different. The main difference is that a 2G TX burst will consume upto 2Amp of peak current, while in 3G burst is more controllable and flat with a peak requirement of 0.8A.

**Potential setup for the power unit:**

![](https://github.com/particle-iot/electron-powersupply/blob/master/electron-power-blockdia.png)

**Requirements for the PMC:**
 - Programmable input current limit
 - Built-in charger for 3.7V LiPo
 - Ouput current of minimum 1A
 - Power path management (optional)
 - Build-in switcher (optional)
 - Small footprint

**List of ICs under evaluation:**
- [BQ24298] (http://www.ti.com/lit/ds/symlink/bq24298.pdf) complete PMC from TI
- [LTC3567] (http://cds.linear.com/docs/en/datasheet/3567f.pdf) compete PMC from LT
- [BQ24030] (http://www.ti.com/lit/ds/symlink/bq24030.pdf) complete PMC - currently used on the power shield
- [TPS62750] (http://www.ti.com/lit/ds/symlink/tps62750.pdf) only a regulator
