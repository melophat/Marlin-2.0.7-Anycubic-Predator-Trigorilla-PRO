# Marlin 3D Printer Firmware

![GitHub](https://img.shields.io/github/license/marlinfirmware/marlin.svg)
![GitHub contributors](https://img.shields.io/github/contributors/marlinfirmware/marlin.svg)
![GitHub Release Date](https://img.shields.io/github/release-date/marlinfirmware/marlin.svg)
[![Build Status](https://github.com/MarlinFirmware/Marlin/workflows/CI/badge.svg?branch=bugfix-2.0.x)](https://github.com/MarlinFirmware/Marlin/actions)

<img align="right" width=175 src="buildroot/share/pixmaps/logo/marlin-250.png" />

Additional documentation can be found at the [Marlin Home Page](https://marlinfw.org/).
Please test this firmware and let us know if it misbehaves in any way. Volunteers are standing by!

## How compile and flash Trigorilla Pro

## ¿What do you need?
 - Just an USB type-A cable included with your printer

## Steps to build, prepare and flash the board
 1. Everything is preconfigured to work with the stock version, if it's your first time compiling Marlin, this can help you [How compile Marlin Tutorial](https://marlinfw.org/docs/basics/install_platformio_vscode.html)
 2. If you got some errors, try use [Auto Build Marlin](https://marlinfw.org/docs/basics/install_platformio.html#auto-build-marlin)
  - If you get an error like `Error: [Errno 2] No such file or directory` make sure the directory string is not too long.
 3. **Turn off and disconnect AC power**
 4. Move the jumper **SW1** to **USB** and **remove JP1 jumper** ![welded cables](/Images/JUMPERS.png)
    - **JP1** It is connected to the pin BOOT0, which blocks the programming, it should be removed.
    - **SW1** Power the board from the USB port or from the external 24V source, for security purposes change this position at least while doing the programming.
 5. Download [STM32 Flasher](https://www.st.com/en/development-tools/flasher-stm32.html#get-software) 
 6. **See this video**
 - [![Trigorilla Pro reflash to Marlin 2.0.x](https://img.youtube.com/vi/g2cAJXle6t0/0.jpg)](https://www.youtube.com/watch?v=g2cAJXle6t0 "ANYCUBIC Predator original board Trigorilla Pro reflash to Marlin 2.0.x")    
 7. **Restores all jumpers to their original position** 
 8. **Finished!**
 
## Backup and restore.
 - As you saw in the video, it is possible to make a backup of your stock firmware. in case you did not, in the precompiled folder, you will find this backup. The flash process is the same seen in the video.


## How compile and flash Trigorilla Pro with ST-Link (Optional)

- ## ¿What do you need?
 - ST-LINK USB debugger or ST development board like NUCLEO Boards
 - [STM32 ST-LINK Utility](https://www.st.com/en/development-tools/stsw-link004.html#get-software)
 - Dupont Jumper cables 
 - Soldering iron
 - Male Pin Header 
 - If you don't know how to weld, go very carefully haha

- ## Steps to build and flash 
 1. Everything is preconfigured to work with the stock version, if it's your first time compiling Marlin, this can help you [How compile Marlin Tutorial](https://marlinfw.org/docs/basics/install_platformio_vscode.html)
 2. If you got some errors, try use [Auto Build Marlin](https://marlinfw.org/docs/basics/install_platformio.html#auto-build-marlin)
 3. **Turn off and disconnect AC power**
 4. Cut and weld jumper cables ![welded cables](/Images/SWD_pins.png)
 5. Move the jumper **SW1** to **USB** and **remove JP1 jumper** ![welded cables](/Images/JUMPERS.png)
    - **JP1** It is connected to the pin BOOT0, which blocks the programming, it should be removed only when the table has the firmware stock. After this it doesn't matter if you put it on or not.
    - **SW1** Power the board from the USB port or from the external 24V source, for security purposes change this position at least while doing the programming.
 6. Connect the SDW pins (SWDIO, SWCLK and GND) to your debugger **don’t need VCC 5v or 3.3v (please don't connect it you could damage your board)**
 7. **Plug the USB** cable on trgirilla pro.
 8. Open STM32 ST-LINK Utility 
   - Open file **(1**) Browse this route `Marlin-Anycubic-Predator-Trigorilla-PRO\.pio\build\trigorilla_pro` and select firmware.bin
   - Click connect to target **(2)**
   - Program verify **(3)**
   - Start **(4)**
   - ![STM32 Utility](/Images/STM32%20ST-LINK%20Utility.png)
 9. **Disconnect usb debugger before testing or motors will stutter, returns the jumpers JP1 and SW1 to the initial position**
 10. **Finished!**

## Marlin 2.0

Marlin 2.0 takes this popular RepRap firmware to the next level by adding support for much faster 32-bit and ARM-based boards while improving support for 8-bit AVR boards. Read about Marlin's decision to use a "Hardware Abstraction Layer" below.

Download earlier versions of Marlin on the [Releases page](https://github.com/MarlinFirmware/Marlin/releases).

## Building Marlin 2.0

To build Marlin 2.0 you'll need [Arduino IDE 1.8.8 or newer](https://www.arduino.cc/en/main/software) or [PlatformIO](http://docs.platformio.org/en/latest/ide.html#platformio-ide). Detailed build and install instructions are posted at:

  - [Installing Marlin (Arduino)](http://marlinfw.org/docs/basics/install_arduino.html)
  - [Installing Marlin (VSCode)](http://marlinfw.org/docs/basics/install_platformio_vscode.html).

### Supported Platforms

  Platform|MCU|Example Boards
  --------|---|-------
  [Arduino AVR](https://www.arduino.cc/)|ATmega|RAMPS, Melzi, RAMBo
  [Teensy++ 2.0](http://www.microchip.com/wwwproducts/en/AT90USB1286)|AT90USB1286|Printrboard
  [Arduino Due](https://www.arduino.cc/en/Guide/ArduinoDue)|SAM3X8E|RAMPS-FD, RADDS, RAMPS4DUE
  [LPC1768](http://www.nxp.com/products/microcontrollers-and-processors/arm-based-processors-and-mcus/lpc-cortex-m-mcus/lpc1700-cortex-m3/512kb-flash-64kb-sram-ethernet-usb-lqfp100-package:LPC1768FBD100)|ARM® Cortex-M3|MKS SBASE, Re-ARM, Selena Compact
  [LPC1769](https://www.nxp.com/products/processors-and-microcontrollers/arm-microcontrollers/general-purpose-mcus/lpc1700-cortex-m3/512kb-flash-64kb-sram-ethernet-usb-lqfp100-package:LPC1769FBD100)|ARM® Cortex-M3|Smoothieboard, Azteeg X5 mini, TH3D EZBoard
  [STM32F103](https://www.st.com/en/microcontrollers-microprocessors/stm32f103.html)|ARM® Cortex-M3|Malyan M200, GTM32 Pro, MKS Robin, BTT SKR Mini
  [STM32F401](https://www.st.com/en/microcontrollers-microprocessors/stm32f401.html)|ARM® Cortex-M4|ARMED, Rumba32, SKR Pro, Lerdge, FYSETC S6
  [STM32F7x6](https://www.st.com/en/microcontrollers-microprocessors/stm32f7x6.html)|ARM® Cortex-M7|The Borg, RemRam V1
  [SAMD51P20A](https://www.adafruit.com/product/4064)|ARM® Cortex-M4|Adafruit Grand Central M4
  [Teensy 3.5](https://www.pjrc.com/store/teensy35.html)|ARM® Cortex-M4|
  [Teensy 3.6](https://www.pjrc.com/store/teensy36.html)|ARM® Cortex-M4|
  [Teensy 4.0](https://www.pjrc.com/store/teensy40.html)|ARM® Cortex-M7|
  [Teensy 4.1](https://www.pjrc.com/store/teensy41.html)|ARM® Cortex-M7|

## Submitting Changes

- Submit **Bug Fixes** as Pull Requests to the ([bugfix-2.0.x](https://github.com/MarlinFirmware/Marlin/tree/bugfix-2.0.x)) branch.
- Follow the [Coding Standards](http://marlinfw.org/docs/development/coding_standards.html) to gain points with the maintainers.
- Please submit your questions and concerns to the [Issue Queue](https://github.com/MarlinFirmware/Marlin/issues).

## Marlin Support

For best results getting help with configuration and troubleshooting, please use the following resources:

- [Marlin Documentation](http://marlinfw.org) - Official Marlin documentation
- [Marlin Discord](https://discord.gg/n5NJ59y) - Discuss issues with Marlin users and developers
- Facebook Group ["Marlin Firmware"](https://www.facebook.com/groups/1049718498464482/)
- RepRap.org [Marlin Forum](http://forums.reprap.org/list.php?415)
- [Tom's 3D Forums](https://forum.toms3d.org/)
- Facebook Group ["Marlin Firmware for 3D Printers"](https://www.facebook.com/groups/3Dtechtalk/)
- [Marlin Configuration](https://www.youtube.com/results?search_query=marlin+configuration) on YouTube

## Credits

The current Marlin dev team consists of:

 - Scott Lahteine [[@thinkyhead](https://github.com/thinkyhead)] - USA &nbsp; [Donate](http://www.thinkyhead.com/donate-to-marlin)
 - Roxanne Neufeld [[@Roxy-3D](https://github.com/Roxy-3D)] - USA
 - Chris Pepper [[@p3p](https://github.com/p3p)] - UK
 - Bob Kuhn [[@Bob-the-Kuhn](https://github.com/Bob-the-Kuhn)] - USA
 - Erik van der Zalm [[@ErikZalm](https://github.com/ErikZalm)] - Netherlands &nbsp; [![Flattr Erik](https://api.flattr.com/button/flattr-badge-large.png)](https://flattr.com/submit/auto?user_id=ErikZalm&url=https://github.com/MarlinFirmware/Marlin&title=Marlin&language=&tags=github&category=software)

## License

Marlin is published under the [GPL license](/LICENSE) because we believe in open development. The GPL comes with both rights and obligations. Whether you use Marlin firmware as the driver for your open or closed-source product, you must keep Marlin open, and you must provide your compatible Marlin source code to end users upon request. The most straightforward way to comply with the Marlin license is to make a fork of Marlin on Github, perform your modifications, and direct users to your modified fork.

While we can't prevent the use of this code in products (3D printers, CNC, etc.) that are closed source or crippled by a patent, we would prefer that you choose another firmware or, better yet, make your own.
