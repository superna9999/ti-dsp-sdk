# TI DM81XX Linux DSP Support Builder #

## Instructions ##

Create directory :

```
$ mkdir dsp
$ cd dsp
$ repo init -u https://github.com/superna9999/ti-dsp-sdk.git -m default.xml
$ repo sync
```

## Generate a kernel and a rootfs with Syslink module, loader and examples ##

```
$ make
```

It will generate:
 * all the kernel files in linux/deploy
 * a rootfs overlay in install directory
 * a complete rootfs in rootfs.tar
 * the toolchain used to build in linux/dl

You are free to use whatever rootfs and pick files from install directory.

