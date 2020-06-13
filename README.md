# [KISS Linux](https://k1ss.org/) for aarch64

This is a repository containing an unofficial port of [KISS Linux](https://k1ss.org/) to [aarch64](https://en.wikipedia.org/wiki/ARM_architecture#AArch64).  The tarball is built for generic aarch64, currently being tested on the [Pinebook Pro](https://www.pine64.org/pinebook-pro/).

![KISS Linux aarch64 screenshot](https://raw.githubusercontent.com/jedavies-dev/kiss-aarch64/master/screenshot3.png "KISS Linux aarch64")

# Installation
You can install the [root tarball](https://github.com/jedavies-dev/kiss-aarch64/releases/download/0.1.6/kiss-chroot-aarch64.tar.xz) from another distro, same as on x86_64.  See https://k1ss.org/install for general installation details.

## Pinebook Pro instructions
Create a partition on the eMMC drive or SD card, format, extract the tarball to it (using sudo!), then write the bootloader files to the drive.  

### Installing the bootloader

Drive allocation on the Pinebook Pro:

| Device  | Description |
| ------------- | ------------- |
| /dev/mmcblk1  | Internal eMMC drive  |
| /dev/mmcblk2  | SD Card reader  |


Using /dev/mmcblk1 as an example:
```
kiss b uboot
kiss i uboot
cd /boot
sudo dd if=idbloader.img of=/dev/mmcblk1 seek=64
sudo dd if=u-boot.itb of=/dev/mmcblk1 seek=16384
mkimage -A arm -O linux -T script -C none -n "U-Boot boot script" -d boot.txt boot.scr
```

### After installation

The tarball is built with generic options. Once installed you can rebuild core with CFLAGS appropriate for the machine:
```
export CFLAGS="-mtune=cortex-a72.cortex-a53 -mcpu=cortex-a72.cortex-a53 -pipe -O2"
export CXXFLAGS=$CFLAGS
export MAKEFLAGS="-j5"
cd /var/db/kiss/installed
kiss b *
```
Add the environment variables to your .profile to persist them.

