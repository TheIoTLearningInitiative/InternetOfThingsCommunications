# BlueZ

> BlueZ is a Bluetooth stack for Linux kernel-based family of operating systems. Its goal is to program an implementation of the Bluetooth wireless standards specifications for Linux. As of 2006, the BlueZ stack supports all core Bluetooth protocols and layers.[2] It was initially developed by Qualcomm, and is available for Linux kernel versions 2.4.6 and up. In addition to the basic stack, the bluez-utils and bluez-firmware packages contain low level utilities such as dfutool which can interrogate the Bluetooth adapter chipset to determine whether its firmware can be upgraded. [Wikipedia](https://en.wikipedia.org/wiki/Bluetooth_stack)

Components

- HCI Core
- HCI UART, USB and Virtual HCI device drivers
- L2CAP module
- Configuration and testing utilities

## Bluez Service

```sh
root@edison:~# systemctl status bluetooth
● bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled)
   Active: active (running) since Sat 2016-07-16 16:56:29 UTC; 50min ago
     Docs: man:bluetoothd(8)
 Main PID: 202 (bluetoothd)
   Status: "Running"
   CGroup: /system.slice/bluetooth.service
           └─202 /usr/lib/bluez5/bluetooth/bluetoothd -E

Jul 16 16:59:39 edison bluetoothd[202]: Error adding Link Loss service
Jul 16 16:59:39 edison bluetoothd[202]: Not enough free handles to register ...e
Jul 16 16:59:39 edison bluetoothd[202]: Not enough free handles to register ...e
Jul 16 16:59:39 edison bluetoothd[202]: Not enough free handles to register ...e
Jul 16 16:59:39 edison bluetoothd[202]: Current Time Service could not be re...d
Jul 16 16:59:39 edison bluetoothd[202]: gatt-time-server: Input/output error (5)
Jul 16 16:59:39 edison bluetoothd[202]: Not enough free handles to register ...e
Jul 16 16:59:39 edison bluetoothd[202]: Not enough free handles to register ...e
Jul 16 16:59:39 edison bluetoothd[202]: Failed to read advertising features:...)
Jul 16 16:59:39 edison bluetoothd[202]: hci0 Load Connection Parameters fail...)
Hint: Some lines were ellipsized, use -l to show in full.
root@edison:~# 
```

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
