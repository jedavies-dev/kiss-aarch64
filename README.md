# kiss-aarch64
KISS Linux running on ARM 64-bit

```Work in progress```

This is a repo for KISS Linux packages that are modified to work on aarch64.  Currently this is running on a [Pinebook Pro](https://www.pine64.org/pinebook-pro/).  

Of the ```core``` set of packages, only 3 have had to be patched.  There will probably be more as I work through the other repos.

# Installation
You can install the [root tarball](https://github.com/jedavies-dev/kiss-aarch64/releases/download/0.1/kiss-chroot.tar.xz) from another distro, same as on x86_64.  See https://getkiss.org/pages/install for details.

For example on the Pinebook Pro, using the preinstalled Debian running on the eMMC drive, it is possible to install KISS to an SD card or the NVME drive.  However booting into the installed KISS environment is currently difficult, involving building of ARM firmware etc.  This is because there is currently no standard way of booting on ARM devices, unlike on x86 machines with BIOS/UEFI.  Details on how to create a boot environment will be added shortly - initial release is made available for feedback purposes only.
