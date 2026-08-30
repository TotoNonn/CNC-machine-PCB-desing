# **Problems and solutions**
## Version 1 of PCB_DRV & PCB_MCU. Driver Configuration.
In the first version, the error that I found was a problem with the drivers. The drivers are modules based on the IC TMC2209-LA. TMC2209 V985 module had a different pinout compared to other TMC2209 modules, because the TMC2209 V985 module was made by a Chinese customer, and they put the UART pin in the place of SPREAD, my mistake was trusting a generic image of internet and trusting my module symbol and footprint in KiCad:

![Generic Image of pinout of TMC2209.](http://microcontrollerslab.com/wp-content/uploads/2021/03/TMC2209-Stepper-Motor-Driver-module-interfacing-with-microcontroller.jpg)

In KiCad my symbol and footprint are exactly the same, then I put the pin UART from the ESP32 to the pin named as a RX in the image (in KiCad the pin name is UART) 

![Symbol in KiCad](image.png)

Here is a correct PINOUT of the TMC 2209 V985 module. I found this in a [Arduino forum](https://forum.arduino.cc/t/trouble-getting-tmc2209-uart-work-with-arduino/1410038/9).

![PINOUT of the TMC 2209 V985 module](image-1.png)

Fine, I just remove the R1 in PCB_DRV and replace with a wire and I made a short betwen pin 12 and 13 in TMC 2209 V985 module because the pin 12 is not conected to the chip in the module I comprobe that whit a multimeter in continuity also I added the reistor betwen RX2 and TX2 in the ESP32 for UART comunication