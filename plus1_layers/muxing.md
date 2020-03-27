# [Yocto Layers](/plus1_layers): sp7021 Flexible Muxing

Is the feature that allow you to change functionality of **ANY** pin 
at the run-time. Flexible muxing is available for:
- both Eth interfaces and MDIO bus;
- SDIO, 8x PWMs, 4x ICMs, 4x SPI masters, 4x SPI Slaves, 4x I2C Masters;
- 4x UARTs;

Group Pin Muxing is available for:
- Audio, SPI Flash, EMMC, USBs;
- LCDIF, FPGA;

## Linux Run-Time Mux
Curent mux information is available at:
```
# cat /sys/bus/platform/devices/9c000100.pctl/txt_map
```
Individual pin/group muxing may be done by running
```
# echo -e "\0xNN" > /sys/bus/platform/devices/9c000100.pctl/<func>
```
, where NN is hex pin number, <func> is the function.

Flexible mux driver supports bulk muxing and onboot firmware load.
