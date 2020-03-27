# [Yocto Layers](/plus1_layers): HowTo : Packaging

## Private packaging system and packaging delivery

> I need private packaging system and packaging delivery

It is very easy to setup repo like [LTPP3G2 repo](https://tibbo.com/downloads/LTPS/repo/)
and syncronize from your Yocto builds.
You need the script "sync.sh" from images/tppg2/ and very basic RSYNC on the 
server.

### RSYNC server setup
```
# dnf install rsync
```
Create rsyncd config file (/etc/rsyncd.conf):
```
$ vi /etc/rsyncd.conf 
secrets file = /etc/rsyncd.secrets
read only = no

[down_ltps_packets]
    path = /mnt/disk/LTPS/downloads/LTPS/packets/
    auth users = down
```
Setup /etc/rsyncd.secrets file for user/password access:
```
$ vi /etc/rsyncd.secrets
myuser:userpass
```
And set rsyncd to start on bootup or setup socket-actived service.

### Refreshing packages index
After your images build you will have each and every packet from DEPEND or 
IMAGE_INSTALL variables in /disk2/build.24/tmp/deploy/rpm/.

Refresh the packages index files before pushing the updates to the server:
```
$ bitbake package-index
```

### Pushing packets to your server
```
$ cd /disk2/build.24/tmp/deploy/images/tppg2/
$ ./sync.sh
```
Script will push the updates of your /disk2/build.24/tmp/deploy/rpm/
directory to your server.

### Customizations

#### Changing URL of your packages repo

At https://github.com/tibbotech/yocto_layers/blob/master/meta-tibbo/conf/distro/tps.conf
variable: PACKAGE_FEED_...

#### Changing package format

At https://github.com/tibbotech/yocto_layers/blob/master/c.tppg2/conf/local.conf
variable: PACKAGE_CLASSES

* RPM is the robist, IPK is the simplest
