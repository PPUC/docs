# PPUC-DMD

PPUC-DMD is a ZeDMD capable of displaying Serum v1 and v2 colorizations on real pinball machines. 

## The hardware components
Currently the hardware consists out of 4 main components:

- Raspberry Pi Zero 2W
- RP2040
- ESP32-S3-N16R8
- PPUC-DMD Carrier PCB

> **IMPORTANT!**
>
> During the distribution of PPUC-DMD units between July 2025 and November 2025, two main variants have been in circulation. One is a PPUC-DMD Carrier PCB with a Raspberry Pi Pico attached via soldered pin headers (REV. 1A & REV. 1B), while the other has the Pico directly integrated into the carrier board (REV. 1C). The software update procedure differs slightly between these two versions, so please pay attention to which variant you are working with.

See both variants here: 

![rev1a](../images/hardware/ppuc-dmd_rev1a.png)
![rev1c](../images/hardware/ppuc-dmd_rev1c.png)

## The software components
PPUC-DMD consists out of 3 seperate software pieces:

* DMDreader (Pico/RP2040)
  * Reads DMD frames and sends to ZeDMDos
* ZeDMDos (Raspberry Pi Zero 2W)
  * Colorizes the DMD frames and sends data to ZeDMD
* ZeDMD (ESP32-S3-N16R8)
  * Sends out color data to the RGB panels

## Updating the software
Updating the software of PPUC/DMD is rather simple. 
First, we will start by updating DMDreader. This runs on the tiny RP2040 chip. 
Secondly, ZeDMDos should be updated. For this we will need the Micro SD card that is currently inserted into the Raspberry Pi Zero 2W.
Optionally ZeDMD can be updated, although there is no noticeable change with the latest release, so don't bother for now. 

### Updating DMDreader
1. Download the latest file. This file is what will be flashed  onto the RP2040 chip. [Click this link to download file.](https://github.com/PPUC/dmdreader/actions/runs/19395571634/artifacts/4578343442) You should now have a file named `dmdreader.uf2`
2. Grab a USB cable. For most this will be a USB-C to USB-A cable. Others might need Micro USB to USB-A. 
3. Make sure game is turned off, in case of owning a REV. 1A or REV. 1B board, you must remove the Raspberry Pi Pico/RP2040 from the PPUC/DMD carrier PCB! (This is the tiny green board) When owning a REV. 1C board, you can lay the DMD down for easy access.
4. On the RP2040/Pico microcontroller and REV. 1C board, you'll find a button labeled `BOOTSEL`. This button enables the software flashing mode. [Watch this video for a demonstration!](https://www.youtube.com/watch?v=os4mv_8jWfU) To enter this mode, hold down the `BOOTSEL` button while connecting the USB cable from your computer to the RP2040/Pico. Once connected, a folder should appear on your computer named `RP2-B2`.
5. Drag and drop the `dmdreader.uf2` file into that folder, which was obtained in step 1. Wait a few seconds until the `RP2-B2` folder closes. 
6. End of DMDreader flashing. Remove USB cable and in cases of REV. 1A/B boards, plug the RP2040/Pico back into the PPUC/DMD carrier board. Make sure all pins line up correctly! 

### Updating ZeDMDos
1. Obtain