# This repo is now archived.
Please check [Glasnost Linux](https://glasnost.org/) if you want to run KISS Linux on other architectures.


# [KISS Linux](https://k1sslinux.org/) for aarch64

This is a repository containing an unofficial port of [KISS Linux](https://k1sslinux.org/) to [aarch64](https://en.wikipedia.org/wiki/ARM_architecture#AArch64).  The tarball is built for generic aarch64, currently being tested on the [Pinebook Pro](https://www.pine64.org/pinebook-pro/).

![KISS Linux aarch64 screenshot](https://raw.githubusercontent.com/jedavies-dev/kiss-aarch64/master/screenshot3.png "KISS Linux aarch64")

# Installation
You can install the [root tarball](https://github.com/jedavies-dev/kiss-aarch64/releases/download/0.1.7/kiss-chroot-aarch64.tar.xz) from another distro, same as on x86_64.  See https://k1sslinux.org/install for general installation details.

Note that you should check this repo onto your machine instead of the main KISS repo.  **This repo includes the main KISS repo as a submodule.** Once you've checked out this repo to your machine, your KISS_PATH should look something like this:

``/home/myuser/kiss-aarch64/core:/home/myuser/kiss-aarch64/overrides:/home/myuser/kiss-aarch64/extra:/home/myuser/kiss-aarch64/modules/repo/extra:/home/myuser/kiss-aarch64/modules/repo/xorg``

When first checking out the repo and you've set your KISS_PATH, be sure to run `kiss u` before building anything. This is to ensure the modules are checked out.

## Pinebook Pro instructions
Create a partition on the eMMC drive or SD card, format, extract the tarball to it (using sudo), then write the bootloader files to the drive.  

### Building a kernel
The Manjaro kernel is currently based on Linux 5.7 with patches for the Pinebook Pro: https://gitlab.manjaro.org/tsys/linux-pinebook-pro

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

### Suggested build flags for Pinebook Pro

```
export CFLAGS="-march=armv8-a+crc+simd+crypto-pipe -O2"
export CXXFLAGS=$CFLAGS
export MAKEFLAGS="-j5"
```
Add the environment variables to your .profile to persist them.


# FAQ
## How come this repo isn't updated very often? Is it behind x86_64 KISS?
This repo includes the main KISS Linux repo as a module.  Therefore whenever the main x86_64 repo is updated, this repo receives those updates also. There is no need for me to check version updates etc. to this repo - you will receive updates from the main KISS repo automatically.

## Is Rust/Firefox provided?
Not currently. I do not have time to maintail an aarch64-musl tarball since I am spending more time on [glasnost](https://glasnost.org/). Using a bootstrap from Void or Alpine may be possible in future.

## How do I build a kernel for my device?
Since the hardware configuration of ARM devices varies greatly, this will depend on your device. A good place to start is to determine what kernel your device is currently using (e.g. under some other distro).  Is it a mainline kernel or a fork? You can copy the config from /proc/config.gz to build a new kernel, or you may be able to boot using a pre-built kernel from another distro. Bootloaders also will vary a lot across devices, so a good starting point is to check the setup of a known working distro for your device.
