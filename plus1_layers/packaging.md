# Yocto Layers: HowTo : Packaging

## Private packaging system and packaging delivery

> I need private packaging system and packaging delivery

It is very easy to setup repo like [LTPP3G2 repo](https://tibbo.com/downloads/LTPS/repo/)
and syncronize from your Yocto builds.
You need the script "sync.sh" from images/tppg2/ and very basic RSYNC on the 
server.
Setup rsync server:
```
# dnf install rsync
```
