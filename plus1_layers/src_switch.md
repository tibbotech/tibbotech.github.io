# [Yocto Layers](/plus1_layers): Switching between Tibbo (release) and SunPlus (dev) repos

There are several repos (bootloaders and kernel) hosted in two locations:

* SunPlus "development" repos hosted internally, accessible with key by request;
* Tibbo "release" repos are hosted at GitHub, publicly available;

Public Tibbo repos are used by default.

To switch between source change values at

<https://github.com/tibbotech/yocto_layers/blob/master/meta-tibbo/conf/machine/include/tppg2-all-prefs.inc>

and rebuild the image:
```
bitbake -c cleanall virtual/kernel && bitbake <imgname>
```

For internal git access request please write to Longson Huang <longsonh@sunplus.com>.
