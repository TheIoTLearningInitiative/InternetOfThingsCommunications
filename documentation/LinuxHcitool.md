# HCITool

- [Adafruit Learn HCITool](https://learn.adafruit.com/search?q=hcitool&)

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

# HCIConfig

```sh
root@edison:~# hciconfig 
hci0:   Type: BR/EDR  Bus: UART
        BD Address: 98:4F:EE:04:1A:8C  ACL MTU: 1021:8  SCO MTU: 64:1
        DOWN 
        RX bytes:4219 acl:26 sco:0 events:120 errors:0
        TX bytes:3944 acl:24 sco:0 commands:75 errors:0

root@edison:~# 
```

```sh
root@edison:~# hciconfig hci0 up
root@edison:~# hciconfig hci0 leadv 3
root@edison:~# hciconfig hci0 noscan
```

```sh
root@edison:~# hciconfig 
hci0:   Type: BR/EDR  Bus: UART
        BD Address: 98:4F:EE:04:1A:8C  ACL MTU: 1021:8  SCO MTU: 64:1
        UP RUNNING 
        RX bytes:4866 acl:26 sco:0 events:156 errors:0
        TX bytes:4696 acl:24 sco:0 commands:111 errors:0

root@edison:~# 
```

```sh
root@edison:~# hcitool -i hci0 cmd 0x08 0x0008 1E 02 01 1A 1A FF 4C 00 02 15 E2 0A 39 F4 73 F5 4B C4 A1 2F 17 D1 AD 07 A9 61 00 00 00 00 C8 00
root@edison:~# 
```
