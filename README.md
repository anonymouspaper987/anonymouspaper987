# Supplementary Material

This repository is the supplementary material to our paper submitted to EuroSys'21 (paper id: 104).
We release a Docker image of 2 generated QEMU machines and 4 firmware used in our evaluation.

## Usage of Docker Image to Boot Kernels

Enter the container.
```
git clone https://github.com/anonymouspaper987/anonymouspaper987.git
sudo apt install -y docker.io docker-compose
sudo docker-compose pull anonymouspaper987
sudo docker-compose up -d
sudo docker-compose run anonymouspaper987 /bin/bash
```

After entering the container,
```
cd example-01 && ./boot.sh 
cd example-02 && ./boot.sh
cd example-03 && ./boot.sh
cd example-04 && ./boot.sh
```
Note that 
+ the username is `root` and the password is empty
+ to quit the QEMU, just enter `ctrl-a x` (enter ctrl and a at the same time, then x)

##  Quick Glance

+ Boot the Linux kernel of embedded firmware.
![](./example-01.png)

## Description of 4 Examples

||Subtarget|Linux kernel version of machine model|Compatible of device tree|Linux kernel version of firmware|
|:-:|:-:|:-:|:-:|:-:|
|example-01|ath79/generic|4.14.167|"comfast,cf-e120a-v3", "qca,ar9344"|4.14.162|
|example-02|ath79/generic|4.14.167|"tplink,archer-c7-v2", "qca,qca9558"|4.14.167|
|example-03|oxnas/generic|3.18.20|"plxtech,nas7820", "plxtech,nas782x"|3.18.20|
|example-04|oxnas/generic|3.18.20|"plxtech,nas7820", "plxtech,nas782x"|3.18.23|

## Highlights of 4 Examples

### Example-01

+ The device tree of the firmware shows the SoC is "comfast,cf-e120a-v3" which is compatible with "qca,ar9344".
```
root@413131ee5739:~/example-01# # after entering the docker
root@413131ee5739:~/example-01# head B7EC64.dts
/dts-v1/;

/ {
        #address-cells = <0x1>;
        #size-cells = <0x1>;
        compatible = "comfast,cf-e120a-v3", "qca,ar9344";
        model = "COMFAST CF-E120A v3";

        interrupt-controller {
                compatible = "qca,ar7100-cpu-intc";
```

+ Boot the Linux kernel of this firmware.
![](./example-01.png)

+ This firmware was compiled with Linux kernel 4.14.162 on 01/06/2020.
```
# # after entering the shell
# cat /proc/version
Linux version 4.14.162 (builder@buildhost) (gcc version 7.5.0 (OpenWrt GCC 7.5.0 r10860-a3ffeb413b)) #0 Mon Jan 6 16:47:09 2020
```

### Example-02

+ The device tree of the firmware shows the SoC is "ctplink,archer-c7-v2" which is compatible with "qca,qca9558".
```
root@413131ee5739:~/example-02# # after entering the docker
root@413131ee5739:~/example-02# head B86264.dts
/dts-v1/;

/ {
        #address-cells = <0x1>;
        #size-cells = <0x1>;
        compatible = "tplink,archer-c7-v2", "qca,qca9558";
        model = "TP-Link Archer C7 v2";

        interrupt-controller {
                compatible = "qca,ar7100-cpu-intc";
```

+ This firmware was compiled with Linux kernel 4.14.167 on 01/29/2020.
```
# # after entering the shell
# cat /proc/version
Linux version 4.14.167 (builder@buildhost) (gcc version 7.5.0 (OpenWrt GCC 7.5.0 r10911-c155900f66)) #0 Wed Jan 29 16:05:35 2020
```

+ Boot the Linux kernel of this firmware.
![](./example-02.png)

### Example-03

+ The device tree of the firmware shows the SoC is "plxtech,nas7820" which is compatible with "plxtech,nas782x".
```
root@413131ee5739:~/example-03# # after entering the docker
root@413131ee5739:~/example-03# head 379B54.dts
/dts-v1/;

/ {
        #address-cells = <0x1>;
        #size-cells = <0x1>;
        compatible = "plxtech,nas7820", "plxtech,nas782x";
        interrupt-parent = <0x1>;
        model = "MitraStar Technology Corp. STG-212";

        chosen {
```

+ Boot the Linux kernel of this firmware.
![](./example-03.png)

+ This firmware was compiled with Linux kernel 3.18.20 on 09/04/2015.
```
# # after entering the shell
# cat /proc/version
Linux version 3.18.20 (buildbot@builder1) (gcc version 4.8.3 (OpenWrt/Linaro GCC 4.8-2014.04 r46450) ) #2 SMP Fri Sep 4 18:53:52 CEST 2015
```

### Example-04

+ The device tree of the firmware shows the SoC is "plxtech,nas7820" which is compatible with  "plxtech,nas782x".
```
root@413131ee5739:~/example-04# # after entering the docker
root@413131ee5739:~/example-04# head 39F784.dts
/dts-v1/;

/ {
        #address-cells = <0x1>;
        #size-cells = <0x1>;
        compatible = "plxtech,nas7820", "plxtech,nas782x";
        interrupt-parent = <0x1>;
        model = "Pogoplug Pro";

        chosen {
```

+ Boot the Linux kernel of this firmware.
![](./example-04.png)

+ This firmware was compiled with Linux kernel 3.18.23 on 01/31/2016.
```
# # after entering the shell
# cat /proc/version
Linux version 3.18.23 (buildbot@builder1) (gcc version 4.8.3 (OpenWrt/Linaro GCC 4.8-2014.04 r47269) ) #2 SMP Sun Jan 31 13:47:55 CET 2016
```
