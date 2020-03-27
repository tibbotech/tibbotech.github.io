# [Yocto Layers](plus1_layers/): HowTo: Clonning

```
git clone git://git.yoctoproject.org/poky.git
cd poky; git checkout origin/zeus;
git clone https://github.com/meta-qt5/meta-qt5.git
cd meta-qt5; git checkout origin/zeus; cd ..
git clone git://git.openembedded.org/meta-openembedded
cd meta-openembedded; git checkout origin/zeus; cd ..
cd ..
git clone https://github.com/tibbotech/yocto_layers.git ./poky.x
rsync -a --exclude=.git ./poky.x/ ./poky/
```
Setup directory for build results. For perfomance (havy i/o) and size (> 50 GB)
reasons it should be on separate hdd:
```
mkdir /disk2
```
