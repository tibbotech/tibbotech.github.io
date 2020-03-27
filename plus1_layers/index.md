# Yocto Layers: HowTo

[Clonning layers](clonning) from GitHub.

[Building](build) the firmware.

Running [BuildApplience](ba)

[Packaging](packaging) your own distribution.

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

Source code example for B chip is there: https://github.com/tibbotech/plus1_Bnoos

It is packed to "nonos" part and included into ISPBOOT.BIN.
Build by ... recipe.

