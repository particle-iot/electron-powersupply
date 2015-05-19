Electron Power - project log
---

**May 19, 2015:**
Maker Faire 2015 was amazing! We are now [Particle!](http://blog.particle.io/2015/05/13/spark-is-now-particle/)

During the craziness of this event, I was still able to make some progress in the Electron domain. There are now two power supply test boards routed up and ready for the fab house. The BQ24298 was mentioned in the previous update, the new one is based around the Maxim MAX8606 which seems to be more widely available compared to the TI variant. I have also included a 3V3 LDO from Richtek, RT9020-33GB, for powering up the microcontroller. 

![](https://github.com/spark/electron-powersupply/blob/master/images/max8606.png)

We are currently looking into a few 3V3 regulators that will power the micro in the second stage. 

LDO:
- RT9020
- TPS735
- MAX8902

Buck-Boost:
- TPS63031
- TPS63051
- RT6150A/B 

**May 6, 2015:**

Designed the PCB for testing the BQ24298 today. I left enough proto area for me to add a buck-boost regulator on this board later when I get to it.

![](https://github.com/spark/electron-powersupply/blob/master/images/bq24298-pcb.png)

**May 6, 2015:**

I'm currently using the TI's BQ24298 as the PMC and leaving the option open to add an LDO or a buck-boost regulator to power the STM32 micro from it. There are some very good options out there for high efficiency regulators. The cellular module can be directly powered from the Vout of the BQ24298 chip since it's within the safe limits (3.5V to 4.35V).

I received some parts I ordered over digikey to breadboard a mock-up of the ublox power consumption under different loads.

>In another news, SpaceX pad abort test was a [success today!!](http://www.spacex.com/news/2015/05/06/crew-dragon-completes-pad-abort-test)

**May 5, 2015:**

The LTC3567 seemed like a lead candidate but it will still require one addional part to bring down the Vout below its max of 4.7V before powering the GSM module. This is a good part since it has a built-in 3V3 switching regulator, but the total cost of the system is signifcantly higher than the TI option.

**Setup 1:**

![setup 1](https://github.com/spark/electron-powersupply/blob/master/images/setup-1.jpg)
---
**Setup 2:**

![setup 2](https://github.com/spark/electron-powersupply/blob/master/images/setup-2.jpg)
---
**Setup 3:**

![setup 3](https://github.com/spark/electron-powersupply/blob/master/images/setup-3.jpg)

I've started designing a board around the TI's BQ24298 chip.

**May 4, 2015:**  
*May the 4th be with you.*  

Identified the minimum requirements for the PMC.
 - Programmable input current limit
 - Built-in charger for 3.7V LiPo
 - Output current of minimum 1A
 - Power path management
 - Build-in switcher (optional)
 - Small footprint

Identified potential parts:
 - BQ24298 complete PMC from TI (ordered an eval board)
 - LTC3567 compete PMC from LT (have an eval board)
 - BQ24030 complete PMC - currently used on the power shield (have an eval board)
 - TPS62750 only a regulator - (have an eval board)  
 
 Ordered parts for building a mock up dummy load to simulate the power requirements of the GSM module. Its essentially a MOSFET with a high wattage load resistor.

 
