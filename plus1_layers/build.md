# [Yocto Layers](/plus1_layers): Building

This is "zeus" branch build commands.
Please look for new version at
[README](https://github.com/tibbotech/yocto_layers) in recommended (default)
branch!

## Get ready for build (should be done once for CLI session)
Open CLI session (console) and do
```
$ cd ./poky/
$ . oe-init-build-env c.tppg2
```

## Build Linux kernel, rootfs and bootloader
In previously opened CLI session (console):
```
$ bitbake img-spmn
```

## Pack generated firmware parts into ISPBOOT.BIN
```
$ cd /disk2/build.24/tmp/deploy/images/tppg2/
$ make -f ./sp_make.mk
```
