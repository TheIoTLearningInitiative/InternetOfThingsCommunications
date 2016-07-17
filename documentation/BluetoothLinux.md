# Linux

- [Man Pages Name sdptool -- Control and interrogate SDP servers](http://linux.die.net/man/1/sdptool)

# HCITool

```sh
root@edison:~# hcitool lescan
LE Scan ...
98:4F:EE:0F:80:FE BatteryMonitorSketch
98:4F:EE:0F:80:FE (unknown)
^Croot@edison:~# 
```

```sh
root@edison:~# hcitool dev
Devices:
        hci0    98:4F:EE:04:1A:8C
root@edison:~# 
```

# Bluez

> BlueZ is a Bluetooth stack for Linux kernel-based family of operating systems. Its goal is to program an implementation of the Bluetooth wireless standards specifications for Linux. As of 2006, the BlueZ stack supports all core Bluetooth protocols and layers.[2] It was initially developed by Qualcomm, and is available for Linux kernel versions 2.4.6 and up. In addition to the basic stack, the bluez-utils and bluez-firmware packages contain low level utilities such as dfutool which can interrogate the Bluetooth adapter chipset to determine whether its firmware can be upgraded. [Wikipedia]()

## Bluez Interface

```sh
root@edison:~# bluetoothctl
[NEW] Controller 98:4F:EE:04:1A:8C MyEdison [default]
[NEW] Device 98:4F:EE:06:1B:99 edison
[NEW] Device 2C:D0:5A:80:7A:44 AARCEMOR-MOBL3
[NEW] Device 98:4F:EE:0F:2B:E0 LED
[NEW] Device E8:B1:FC:09:6A:FE ubuntu-gnome-0
[NEW] Device 40:78:6A:26:4A:C2 XT1008
[bluetooth]# 
```
