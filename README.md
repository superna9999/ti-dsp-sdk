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

The kernel tarballs will be in :
```
linux/deploy/
├── $kernelver-dtbs.tar.gz
├── $kernelver-firmware.tar.gz
├── $kernelver-modules.tar.gz
├── $kernelver.zImage
├── config-$kernelver
```

The syslink kernel module will be in :
```
install/lib/modules/$kernelver/kernel/drivers/dsp/syslink.ko
```

The syslink samples will be in :
```
install/root/examples/
├── ex01_helloworld
│   ├── debug
│   │   ├── app_host
│   │   ├── run.sh
│   │   ├── server_dsp.xe674
│   │   └── slaveloader
│   └── release
│       ├── app_host
│       ├── run.sh
│       ├── server_dsp.xe674
│       └── slaveloader
├── ex02_messageq
│   ├── debug
│   │   ├── app_host
│   │   ├── run.sh
│   │   ├── server_dsp.xe674
│   │   └── slaveloader
│   └── release
│       ├── app_host
│       ├── run.sh
│       ├── server_dsp.xe674
│       └── slaveloader
├── ex03_notify
│   ├── debug
│   │   ├── app_host
│   │   ├── run.sh
│   │   ├── server_dsp.xe674
│   │   └── slaveloader
│   └── release
│       ├── app_host
│       ├── run.sh
│       ├── server_dsp.xe674
│       └── slaveloader
├── ex04_sharedregion
│   ├── debug
│   │   ├── app_host
│   │   ├── run.sh
│   │   ├── server_dsp.xe674
│   │   └── slaveloader
│   └── release
│       ├── app_host
│       ├── run.sh
│       ├── server_dsp.xe674
│       └── slaveloader
├── ex05_heapbufmp
│   ├── debug
│   │   ├── app_host
│   │   ├── run.sh
│   │   ├── server_dsp.xe674
│   │   └── slaveloader
│   └── release
│       ├── app_host
│       ├── run.sh
│       ├── server_dsp.xe674
│       └── slaveloader
├── ex06_listmp
│   ├── debug
│   │   ├── app_host
│   │   ├── run.sh
│   │   ├── server_dsp.xe674
│   │   └── slaveloader
│   └── release
│       ├── app_host
│       ├── run.sh
│       ├── server_dsp.xe674
│       └── slaveloader
├── ex07_gatemp
│   ├── debug
│   │   ├── app_host
│   │   ├── run.sh
│   │   ├── server_dsp.xe674
│   │   └── slaveloader
│   └── release
│       ├── app_host
│       ├── run.sh
│       ├── server_dsp.xe674
│       └── slaveloader
├── ex08_ringio
│   ├── debug
│   │   ├── app_host
│   │   ├── run.sh
│   │   ├── server_dsp.xe674
│   │   └── slaveloader
│   └── release
│       ├── app_host
│       ├── run.sh
│       ├── server_dsp.xe674
│       └── slaveloader
└── runall.sh
```

## Technical facts ##

The build uses RobertCNelson's build systems to generate set of linux tarballs, then uses a patched version of syslink package and uses buildroot to generate a minimal rootfs from the linaro toolchain.

