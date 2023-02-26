## QDev Tiny

| Property        | Value             |
| --------------- | ----------------- |
| Revision        | 1                 |
| Microcontroller | ATtiny25/45/85-PU |
| ISP Connector   | Yes               |
| USB Support     | Yes (software)    |
| GPIO Count      | 6 (1 passive)     |

### Description

QDevTiny is a small board that is built around the Atmel ATTiny25/45/85 microcontroller. It has an 8 pin header, 6 of them being GPIO pins. It also includes an ISP programming header for easy use with Atmel programmers. The board has a USB Type-A male edge connector for power and USB programming. USB programming requires the Micronucleus bootloader (which provides software USB support for certain Atmel microcontrollers) to be flashed.

### Supported Microcontroller Chips

| Microcontroller   | Flash | SRAM | EEPROM |
| ----------------- | ----- | ---- | ------ |
| ATtiny25          | 2KB   | 128B | 128B   |
| ATtiny45          | 4KB   | 256B | 256B   |
| ATtiny85          | 8KB   | 512B | 512B   |

### Setup Instructions

These instructions are for Linux. For other operating systems, the provided commands may be different.

1. To burn the Micronucleus bootloader, you need an Arduino UNO/Mega/Nano or an AVR ISP programmer. Open the `Examples > Arduino ISP` sketch in Arduino IDE, uncomment the line with `#define USE_OLD_STYLE_WIRING` and upload it to your Arduino board.

2. Open the Arduino IDE preferences and add the ATtiny Core library JSON link (http://drazzy.com/package_drazzy.com_index.json) to "Board Manager URLs" section. Wait for the Arduino IDE to process it and then install the ATtiny Core package from the Boards Manager.

3. Wire the QDev Tiny pins to the Arduino for programming.
    - 5V -> VCC
    - GND -> GND
    - 10 -> R/IO5
    - 11 -> IO0
    - 12 -> IO1
    - 13 -> IO2

4. Download the Micronucleus ATtiny85 binary from: https://raw.githubusercontent.com/micronucleus/micronucleus/master/firmware/releases/t85_default.hex

5. Open the terminal  in the folder you downloaded the Micronucleus binary in and run the following command. Replace `/dev/ttyUSB0` with the correct port if necessary.

```sh
sudo avrdude -c arduino -b 19200 -P /dev/ttyUSB0 -p t85 -U flash:w:t85_default.hex -U lfuse:w:0xF1:m -U hfuse:w:0xDD:m -U efuse:w:0xFE:m
```

Micronucleus should now be flashed. Disconnect the programming pins and plug your board into your computer. Check the output of the `lsusb` command. Your board should show up as `MCS Digistump DigiSpark`.

To upload a program to your board via USB, export your program via `Sketch > Export Compiled Binary`. Open the terminal in the build folder of your sketch and run the following command (change "your_program_name.hex" with the hex file of your program):

```sh
avrdude -c micronucleus -p t85 -x wait -V -U flash:w:your_program_name.hex
```

You can also download the Micronucleus CLI tool from https://github.com/micronucleus/micronucleus/releases/tag/v2.6 and use it to upload your programs:

```sh
micronucleus your_program_name.hex
```

You may need to press the reset button before uploading your program.

### Images

![](https://github.com/qewer33/QDev-Boards/blob/main/assets/qdevtiny-3d-board.png?raw=true)

![](https://github.com/qewer33/QDev-Boards/blob/main/assets/qdevtiny-pcb-board.png?raw=true)
