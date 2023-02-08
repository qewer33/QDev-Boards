# QDev Boards

QDev Boards is a series of development boards that are inexpensive, simple and easy to order and assemble for beginner hobbyists.

This repository currently only has one entry but I plan to add more as I design and protoype new boards.

I am still fairly new and inexperienced when it comes to electronics and PCB design so if you have any suggestions or critics, please send them my way.

## QDev Tiny

```markdown
| Revision        | 1                 |
| Microcontroller | ATtiny25/45/85-PU |
| ISP Connector   | Yes               |
| USB Support     | Yes (software)    |
| GPIO Count      | 6 (1 passive)     |
```

### Description

QDevTiny is a small board that is built around the Atmel ATTiny25/45/85 microcontroller. It has an 8 pin header, 6 of them being GPIO pins. It also includes an ISP programming header for easy use with Atmel programmers. The board has a USB Type-A male edge connector for power and USB programming. USB programming requires the Micronucleus bootloader (which provides software USB support for Atmel microcontrollers) to be flashed.

### Supported Microcontroller Chips

```
| Microcontroller   | Flash | SRAM | EEPROM |
| ----------------- | ----- | ---- | ------ |
| ATtiny25          | 2KB   | 128B | 128B   |
| ATtiny45          | 4KB   | 256B | 256B   |
| ATtiny85          | 8KB   | 512B | 512B   |
```

### Images

![](https://github.com/qewer33/QDev-Boards/blob/main/assets/qdevtiny-3d-board.png?raw=true)

![](https://github.com/qewer33/QDev-Boards/blob/main/assets/qdevtiny-pcb-board.png?raw=true)
