# [KISS Linux](https://k1ss.org/) for aarch64

This is a repository containing an unofficial port of [KISS Linux](https://k1ss.org/) to the [aarch64](https://en.wikipedia.org/wiki/ARM_architecture#AArch64) [Pinebook Pro](https://www.pine64.org/pinebook-pro/) platform.

![KISS Linux aarch64 screenshot](https://raw.githubusercontent.com/jedavies-dev/kiss-aarch64/master/screenshot3.png "KISS Linux aarch64")

```Work in progress```


# Installation
You can install the [root tarball](https://github.com/jedavies-dev/kiss-aarch64/releases/download/0.1/kiss-chroot.tar.xz) from another distro, same as on x86_64.  See https://k1ss.org/install for general installation details.

This repo now includes a "uboot" package, which will place the requisite u-boot binaries in /boot.
These can then be written to the device you wish to boot from.  See [this page](https://stikonas.eu/wordpress/2019/09/15/blobless-boot-with-rockpro64/) for details on how to write the u-boot binary to a block device.


For details on building

Next on the todo list:
 - Confirm all packages build, patch where required.
 - Provide detailed instructions on how to create a bootable device.
 - Create bootable image file for flashing to sd/mmc as an alternative installation method.
 - Provide firefox-bin for convenience.
 - More docs (separate website?).
 - Provide instructions on how to run without any binary blobs (it is possible!).
 
