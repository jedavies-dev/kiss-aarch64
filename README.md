# [KISS Linux](https://k1ss.org/) for aarch64

This is a repository containing an unofficial port of [KISS Linux](https://k1ss.org/) to the [aarch64](https://en.wikipedia.org/wiki/ARM_architecture#AArch64) [Pinebook Pro](https://www.pine64.org/pinebook-pro/) platform.

![KISS Linux aarch64 screenshot](https://raw.githubusercontent.com/jedavies-dev/kiss-aarch64/master/screenshot3.png "KISS Linux aarch64")

```Work in progress```


# Installation
You can install the [root tarball](https://github.com/jedavies-dev/kiss-aarch64/releases/download/0.1/kiss-chroot.tar.xz) from another distro, same as on x86_64.  See https://k1ss.org/install for details.

Booting involves flashing u-boot to an SD/MMC drive.  Currently I am using an SD card with u-boot & kernel, with root on the NVMe drive.

Xorg is now working OK.  Also Rust + Firefox now build.

Next on the todo list:
 - Bootable image to flash to sd/mmc
 - Provide firefox-bin for convenience
 - More docs (separate website?)
 
