# Yocto Layers: HowTo

[Clonning layers](clonning) from GitHub.

[Building](build) the firmware.

[Packaging](packaging) your own distribution.

> What is this ISPBOOOT.BIN file, what is the humor here. Is it mandatory or not ?

It is the bootloader+kernel+rootfs packed in one file. Structure is there:
https://sunplus-tibbo.atlassian.net/wiki/spaces/doc/pages/468549641/Plus1+Layout+of+ISPBOOOT.BIN+and+Storage+Devices?preview=%2F468549641%2F467992650%2FPlus1%20Layout%20of%20ISPBOOOT.BIN%20and%20Storage%20Devices.xlsx

If you need to update the whole OS on your board, you need this file.
