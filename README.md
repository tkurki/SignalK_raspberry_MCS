# SignalK_raspberry_MCS
SignalK Plugin to provide MCS functionality to SignalK  
Attention: the postinstall.js scripts need sudo privilegs!

## Overview:  
This package install all dependencies, modules and dt-overlays to provide the fully avalability of the MCS board in SignalK.  
This package only works on a Raspberry Pi with a wired GeDaD MCS (Marine Controll Server).   

https://www.gedad.de/shop/gecos-wired/#cc-m-product-15562399022  

Be careful. The postinstallationscript works with sudo acess! 

## How to install:
Install the SignalK_raspberry_MCS Plugin in the Signalk Appstore.  
After the Installation:
1. Run the postinstallscript:  
```sh
sudo node $HOME/.signalk/node_modules/signalk-raspberry-mcs/postinstall.js
```  
(This script add the dt-overlays for CAN and NMEA0183 to the config.txt, adds the modules and installs and enable the 1-wire service and the autoshutdown service)  

2. Restart your Pi!!!

=> After this steps you can use the signalK Plugin.

## How to use (Plugin)
Plugin overview:  

![Plugin](/data/Picture_MCS_Plugin.png)

After this all should work.. ;-)  

## How to use serial interfaces (NMEA0183)
All 6 serial interfaces should now be availible in the connection tab. You find the unter "Input Type" NMEA0183 , "MMEA0183Source" Serial.  
You can use each interface as "Input" or "Output"  

![Serial](/data/Picture_MCS_Serial.png)  

## How to use CAN (NMEA2000) interface  

You can Setup the caninterface directly in the connections  

![CAN](/data/Picture_MCS_CAN.png)

## How to use 1-wire (DS18B20 temp sensors

You can use more then one sensor on the 1-wire line (see Manual MCS-Board)  
CLick on the add Button. Then you can define the Values of your Sensor. You can use a Sensor (Sensor ID) more then once to assign the value to more then one delta. But do not use a delta more then once!

![owire](/data/Picture_MCS_owire.png)

Fully configurated Sensor:

![owire](/data/Picture_MCS_owire1.png)

Data output:

![owire](/data/Picture_MCS_owire2.png)

The sample rate should be not less then "number of sensors" x 1s = "sample rate"


## How to use a digital input (IN1-IN4) for seatalk1 reading

Since the Seatalk1 GPIO reading is implimented in SignalK, ou can use the inputs for ST1 reading.  
Follow the guidline in the [Seatalk(GPIO).md](https://github.com/SignalK/signalk-server/blob/master/Seatalk(GPIO).md)  
The "Hardware part you can ignore, because it´s done on the MCS board. Only connect the yellow wire to one of the 4 inputs.  
The IN1-IN4 inputs are assignet as follows:
|MCS Input|GPIO|
| ------ | ------ |
|In1|GPIO19|
|In2|GPIO16|
|In3|GPIO26|
|In4|GPIO20|


## General 
Don´t forget to save the plugin settings after changes. ;-)

## Todos
- Add plugin intigration for speed (Hz) measurement through In1-In4
- Add plugin intigration for switch states (Sensors etc.) from the IN1-IN4 to map to delta´s





