# Getting Started

## Planning

If you want to run an existing playfield with PPUC you need to take some decisions:

- Should the original wiring be kept?
- Should lamps (inserts, GI and/ flashers) be replaced by addressable RGB LEDs?
- Should switches be wired using a matrix or directly.
- Which switches should drive coils as fast as possible or directly without involving the CPU?

(Pros ans cons will be described later.)

Multipe boards can be cascaded to to have enough input and output ports. The communication happens via a RS485 BUS and the
protocol enhances the DOF protocol which is known from the virtual pinball world.

## Get IO Boards

Depending on your decisions above, you you might need different IO boards and a different amount.
The entire hardware is open source and you can order the boards from your preferred PCB manufacturer.
Gerber and BOM files are part of the repositories:

- [IO_16_8_1](https://github.com/PPUC/Hardware_IO_16_8_1)
- [IO_16x8_matrix](https://github.com/PPUC/Hardware_IO_16x8_matrix)
- [Out_8X10](https://github.com/PPUC/Hardware_Out_8x10)
- [Opto_16](https://github.com/PPUC/Hardware_Opto_16)

## Wiring the boards

- Power
- RS485 bus
- Coils
- Switches
- Lamps
- Motors

For more details read the [hardware documentation](../ppuc_hardware/index.md).

## Flash the IO Board Firware

To bring "life" into the PPUC boards they need to get some software. All the boards gets the same firmware. Details about what they shall do and what they are connected to, are set by the config file which is generated by the config tool. This will be used to initialize the boards on start up.

The boards are distinguished by an address. This must be set by DIP switches on the board. Every board must have a different address.

Download the latest firmware for your boards from https://github.com/PPUC/io-boards/releases/latest

Press and hold the `Boot` button of your board and connect it to your computer via USB.
Release the button after a removable mass storage device is detected by your computer.
Copy the appropriate `uf2` file from the download above to that mass storage device.
The board will automatically flash the firmware and reboot.
Repeat that procedure for every board.

## "CPU"

The IO boards need a CPU, regardless if you replacing broken or missing electronics or creating a homebrew game.

### PinMAME
The platform independent [PPUC command line tool](https://github.com/PPUC/ppuc) can run on any old or small computer like a Raspberry Pi and leverages libpinmame to emulate the ROM.

### PPUC Config-Tool

[PPUC config-tool](https://github.com/PPUC/config-tool)
