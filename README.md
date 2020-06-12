# [KISS Linux](https://k1ss.org/) for aarch64

This is a repository containing an unofficial port of [KISS Linux](https://k1ss.org/) to [aarch64](https://en.wikipedia.org/wiki/ARM_architecture#AArch64).  The tarball is built for generic aarch64, currently being tested on the [Pinebook Pro](https://www.pine64.org/pinebook-pro/).

![KISS Linux aarch64 screenshot](https://raw.githubusercontent.com/jedavies-dev/kiss-aarch64/master/screenshot3.png "KISS Linux aarch64")

# Installation
You can install the [root tarball](https://github.com/jedavies-dev/kiss-aarch64/releases/download/0.1.6/kiss-chroot-aarch64.tar.xz) from another distro, same as on x86_64.  See https://k1ss.org/install for general installation details.

## Pinebook Pro instructions
Create a partition on the eMMC drive, extract the tarball to it, then write the bootloader files to the drive.  See [this page](https://stikonas.eu/wordpress/2019/09/15/blobless-boot-with-rockpro64/) for details on how to write the u-boot binary to a block device.  The "gcc-baremetal" package is available for building the ARM firmware (atf, uboot).
