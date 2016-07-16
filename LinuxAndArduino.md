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

```sh
[bluetooth]# scan on
Discovery started
[CHG] Controller 98:4F:EE:04:1A:8C Discovering: yes
[NEW] Device 98:0D:2E:CD:84:90 Victoretorotavi
[NEW] Device 60:D8:19:AF:8F:12 CDAVALOX-MOBL
[NEW] Device C8:FF:28:A0:71:1C LAPASXA10W10
[NEW] Device E8:B1:FC:09:6A:FE ubuntu-gnome-0
[NEW] Device 98:4F:EE:06:44:E5 98-4F-EE-06-44-E5
[CHG] Device 98:4F:EE:06:44:E5 RSSI: -64
[CHG] Device 98:4F:EE:06:44:E5 TxPower: 0
[CHG] Device 98:4F:EE:06:44:E5 Name: edison
[CHG] Device 98:4F:EE:06:44:E5 Alias: edison
[CHG] Device 98:4F:EE:06:44:E5 Modalias: usb:v1D6Bp0246d0525
[CHG] Device 98:4F:EE:06:44:E5 UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Device 98:4F:EE:06:44:E5 UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Device 98:4F:EE:06:44:E5 UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Device 98:4F:EE:06:44:E5 UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Device 98:4F:EE:06:44:E5 UUIDs: 0000111e-0000-1000-8000-00805f9b34fb
[CHG] Device 98:4F:EE:06:44:E5 UUIDs: 0000110a-0000-1000-8000-00805f9b34fb
[CHG] Device 98:4F:EE:06:44:E5 UUIDs: 0000110b-0000-1000-8000-00805f9b34fb
[CHG] Device 98:0D:2E:CD:84:90 RSSI: -71
[CHG] Device 98:0D:2E:CD:84:90 RSSI: -71
[CHG] Device 98:4F:EE:0F:2B:E0 Connected: no
[CHG] Device 98:4F:EE:0F:2B:E0 RSSI: -61
[CHG] Device 98:4F:EE:0F:2B:E0 Name: LED
[CHG] Device 98:4F:EE:0F:2B:E0 Alias: LED
[bluetooth]# scan off       
[CHG] Device 98:4F:EE:0F:2B:E0 RSSI is nil
[CHG] Device 98:4F:EE:06:44:E5 TxPower is nil
[CHG] Device 98:4F:EE:06:44:E5 RSSI is nil
[CHG] Device E8:B1:FC:09:6A:FE TxPower is nil
[CHG] Device E8:B1:FC:09:6A:FE RSSI is nil
[CHG] Device C8:FF:28:A0:71:1C TxPower is nil
[CHG] Device C8:FF:28:A0:71:1C RSSI is nil
[CHG] Device 60:D8:19:AF:8F:12 TxPower is nil
[CHG] Device 60:D8:19:AF:8F:12 RSSI is nil
[CHG] Device 98:0D:2E:CD:84:90 TxPower is nil
[CHG] Device 98:0D:2E:CD:84:90 RSSI is nil
Discovery stopped
[CHG] Controller 98:4F:EE:04:1A:8C Discovering: no
[bluetooth]# 
```