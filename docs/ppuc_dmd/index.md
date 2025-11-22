# PPUC-DMD

PPUC-DMD is a ZeDMD capable of displaying Serum colorizations on real pinball machines. 

## The hardware
Currently the hardware consists out of 4 main components:

- Raspberry Pi Zero 2W
- RP2040
- ESP32-S3-N16R8
- PPUC-DMD Carrier PCB

> **IMPORTANT!**
>
> During the distribution of PPUC-DMD units between July 2025 and November 2025, two main variants have been in circulation. One is a PPUC-DMD Carrier PCB with a Raspberry Pi Pico attached via soldered pin headers, while the other has the Pico directly integrated into the carrier board. The software update procedure differs slightly between these two versions, so please pay close attention to which variant you are working with.

See both variants here: 

![rev1a](../images/hardware/ppuc-dmd_rev1a.png)
![rev1c](../images/hardware/ppuc-dmd_rev1c.png)

## The software components
PPUC-DMD consists out of 3 seperate software pieces:

* DMDreader (Pico)
  * Reads DMD frames of real pinball machines and sends to ZeDMDOS
* ZeDMDOS (Raspberry Pi Zero 2W)
  * Colorizes the DMD frames and sends data to ZeDMD
* ZeDMD (ESP32-S3-N16R8)
  * Sends out color data to RGB panels

## Updating the software
Updating the software of PPUC/DMD is rather simple. First, we will start by updating DMDReader. This runs on the tiny RP2040 chip. 

### Updating DMDreader
1. Get the latest file. This file is what will be uploaded to the RP2040 chip to flash the latest firmware. [Click this link to install.](https://github.com/PPUC/dmdreader/actions/runs/19395571634/artifacts/4578343442) Extract the zip file so that you are left with just `dmdreader.uf2`.

2. 