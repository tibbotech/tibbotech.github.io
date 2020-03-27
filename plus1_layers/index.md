# Tibbo Yocto Linux Distribution

Tibbo Yocto Layers at <https://github.com/tibbotech/yocto_layers> is for developers who
want to make they own Linux distribution for they custom board
or for thouse who wants to take part in bootloader/kernel development for 
[Plus1/sp7021](https://tibbo.com/store/plus1.html) SoC.

Tibbo hosts prebuild Yocto Linux for its LTPPxG2 sp7021-based board:
- LTPPxG2 Firmware: <https://tibbo.com/downloads/LTPS/FW/LTPPg2/>
- LTPPxG2 binary packages: <https://tibbo.com/downloads/LTPS/repo/LTPPg2/>
- LTPPxG2 SDK: <https://tibbo.com/downloads/LTPS/SDK/LTPPg2/>
- LTPPxG2 BuildAppliance <https://tibbo.com/downloads/LTPS/BuildAppliance/>

Binary packages is the collection of most necessary packets you may need to use
with LTPPxG2 board. The collection includes Tibbo closed-source packages, like
- [TiOS](https://docs.tibbo.com/taiko/intro_tios) as user-space Linux application.
- [AggreGate](https://aggregate.tibbo.com/) and [AggreGate Agent](https://aggregate.tibbo.com/technology/connectivity/agents.html).
- [Configurator](https://tibbo.com/tps/configurator.html) and device management web interface, etc.

as well, as Python packages, NodeJS modules, JRE, OpenCV, Qt5 libs 
(also included into SDK), various cli utilities.

If you're just an application or external kernel module developer for LTPPxG2 
board then SDK right for your needs.

Take a look at our comprehensive [SDK tutorial](https://tibbo.com/linux/native-c.html).
It describes how to build kernel modules and applications for LTPP platform, 
[SDK + QtCreator](https://tibbo.com/linux/native-c/ide-qt-creator.html)
and
[SDK + Eclipse](https://tibbo.com/linux/native-c/ide-qt-creator.html) usage,
how to run [SDK on Windows 10](https://tibbo.com/linux/native-c/windows.html), etc.

## Plus1 SoC In-depth

If you're curious about SoC technical documentation, please take a look at
[SunPlus/Tibbo Wiki](https://sunplus-tibbo.atlassian.net/wiki/spaces/doc/overview).

Special feature: [Flexible Run-Time Peripheral Multiplexing](muxing) (PinMux) is available in Linux.

## Yocto Layers: HowTo

[Clonning layers](clonning) from GitHub.

[Building](build) the firmware.

Running the [BuildApplience](ba)

[Packaging](packaging) your own distribution.

[Switching](src_switch) between Tibbo (release) and SunPlus (development) repos.

## Qustions and Answers

> I wonder how many year this chip will be produced ?

At least 10 years, starting from 2020.

> What is this ISPBOOOT.BIN file, what is the humor here. Is it mandatory or not ?

It is the bootloader+kernel+rootfs packed in one file. Structure is at [SunPlus/Tibbo wiki](<https://sunplus-tibbo.atlassian.net/wiki/spaces/doc/pages/468549641/Plus1+Layout+of+ISPBOOOT.BIN+and+Storage+Devices?preview=%2F468549641%2F467992650%2FPlus1%20Layout%20of%20ISPBOOOT.BIN%20and%20Storage%20Devices.xlsx)

If you need to update the whole OS on your board, you need this file.

> Is ROM code available?

It is not.
The ROM code is the intellectual property of [SunPlus](https://www.sunplus.com/index.asp).

> What stands for iboot, xboot and relation with uboot ?

iboot is tiny ROM-code, written in C and assembly, fits to 16KB of RAM, started 
first after power on.

xboot is pre-u-boot. It initializes the memory, uart, usb and SD. There are well-known
U-Boot-SPL, but u-boot-SPL is too big to fit into 16KB-space, so we have 
smaller program named XBoot, the replacement for fat U-boot SPL binary.

In short, iboot (ROM) --(emmc/spinand/sd)--> xboot --(+usb)--> u-boot --(+net)--> kernel

> How can I implement Freertos on B-Core on SP7021 (ARM926 Core), or any other RTOS-like operating system?

Source code example for B chip is there: <https://github.com/tibbotech/plus1_Bnoos>

It is packed to "nonos" part and included into ISPBOOT.BIN.
Build by ... recipe.

