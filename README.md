# Sovol SV-01 - Firmware to Enable BlTouch and Filament Sensor
Firmware and Marlin directory that works with BigTreeTech SKR Mini E3 v2.0 and enables filament sensor and BLtouch

## Opening and Compiling:

You will need to setup Visual Studio Code with platform.io and Marlin Auto Builder. You can follow the Teaching Tech guide on how to setup VS Code and open the correct directory.

***Teaching Tech: Marlin and VS Code Setup***
https://www.youtube.com/watch?v=eq_ygvHF29I
[![Teaching Tech: VS Code Setup](https://img.youtube.com/vi/eq_ygvHF29I/0.jpg)](https://www.youtube.com/watch?v=eq_ygvHF29I)


### Steps:

1. Download this repo
2. Once VS Code is setup, unzip this repo zip file.
3. In VS Code, click File > Open. Then select the ***Marlin207*** directory.
4. Follow the steps in the YT video above on how to compile.
5. Once Compiled, put on a microSD card and insert to the SKR mainboard (you likely can upload over USB connection, but thats for you to find out :)

When the new firmware is flashed, check your E-Steps. Mine were way off (M92 listed E93.0, but I needed E411).

***Calibrate E-Steps:***
https://www.youtube.com/watch?v=6PL_rSPZ3M8


Once E-Steps are calibrated, you will need to set your Z-probe offset. Start a bed leveling print and scroll offset to a negative value until you start getting good bed adhesion.

For the filament sensor, start a quick print (XYZ Cube works well) then cut your filament halfway through the print. It should immediately stop and prompt you to change filament. Click go again and you're good to go!


---
*Important Note*: The BTT boards have 256k flash memory so you would normally select the first build option in Auto Build Marlin. When I was compiling, it would fail due to too much space being used. I used the 512k option when building. In the VS Code terminal, it will let you know how much flash storage was used. After using the 512k build, it only uses I have added the current compile size below. This compiles to less than 256k so it works.

```
RAM:   [===       ]  27.2% (used 13376 bytes from 49152 bytes)
Flash: [=====     ]  45.3% (used 237628 bytes from 524288 bytes)
```
*If you divide the 524288/2, that is the SKR flash amount.*
