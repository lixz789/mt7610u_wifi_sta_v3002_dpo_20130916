# mt7610u_wifi_sta_v3002_dpo_20130916
Modified usb wifi driver for TP-Link TL-WDN5200 AC600 T2U and Cisco Linksys AE6000 / AC580 on Linux. 
1. modified:   common/rtusb_dev_id.c 
 * add product id for TL-WDN5200
 * add product id for Cisco Linksys AE6000 / AC580
1. modified:   include/os/rt_linux.h 
1. modified:   os/linux/rt_linux.c
 * fix compile error from struct _OS_FS_INFO_
 * fix problem on 64bit
1. modified:   os/linux/config.mk
 * change default setting for Ubuntu 
1. modified  common/cmm_info.c 
 * fix compile with gcc 4.9.2 newer Kernel (Ubuntu 15.04)

#prepare
Ubuntu: sudo apt-get install git build-essential

#prepare kernel source code
..if you get this error: no rule, for target „arch/arm/tools/syscall.tbl“, 
  needed from „arch/arm/include/generated/uapi/asm/unistd-common.h“
  
  For new kernel versions 5+ you need to download the latest rpi-sources to fix it:

$ sudo wget https://raw.githubusercontent.com/notro/rpi-source/master/rpi-source -O /usr/bin/rpi-source
$ sudo chmod +x /usr/bin/rpi-source
$ /usr/bin/rpi-source -q --tag-update
$ rpi-source
 
 if you get any question just answer with [y]


# how to use
```
$ mkdir ~/src
$ cd ~/src
$ git clone https://github.com/lixz789/mt7610u_wifi_sta_v3002_dpo_20130916.git
$ cd mt7610u_wifi_sta_v3002_dpo_20130916
$ sudo ARCH=arm make -j4
$ sudo ARCH=arm make installfw
$ sudo insmod mt7610u.ko
  or
  sudo insmod mt7630u.ko
  or
  sudo insmod mt7650u.ko
  
$ sudo ARCH=arm make install
$ cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
$ reboot
```
refer to：
http://hprath.com/2014/06/cisco-linksys-ae6000-ac580-media-tek-mt7610u-mt7630u-mt7650u-linux-x64-driver-patch/
On this page you'll find also details about configuration in RT2870STA.dat.

https://github.com/chenhaiq/mt7610u_wifi_sta_v3002_dpo_20130916 (TP-Link T2U)



