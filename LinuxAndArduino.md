# Linux and Arduino

Credits to [Github Daniela Plascencia DnPlas](https://github.com/dnplas)

```sh
root@edison:~# rfkill unblock bluetooth
root@edison:~# bluetoothctl
[NEW] Controller 98:4F:EE:04:1A:8C MyEdison [default]
[NEW] Device 98:4F:EE:0F:2B:E0 ARDUINO 101-2BE0
[NEW] Primary Service
        /org/bluez/hci0/dev_98_4F_EE_0F_2B_E0/service0009
        Vendor specific
[NEW] Characteristic
        /org/bluez/hci0/dev_98_4F_EE_0F_2B_E0/service0009/char000a
        Vendor specific
[NEW] Device 98:4F:EE:06:1B:99 edison
[NEW] Device 2C:D0:5A:80:7A:44 AARCEMOR-MOBL3
[NEW] Device 40:78:6A:26:4A:C2 XT1008
[bluetooth]# 
```