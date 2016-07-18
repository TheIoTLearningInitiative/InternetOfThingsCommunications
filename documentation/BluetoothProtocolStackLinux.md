# Linux

- [Man Pages Name sdptool -- Control and interrogate SDP servers](http://linux.die.net/man/1/sdptool)
- [An Introduction to Bluetooth Programming by Albert Huang](https://people.csail.mit.edu/albert/bluez-intro/index.html)




# L2Ping

```sh
root@edison:~# l2ping E8:B1:FC:09:6A:FE   
Ping: E8:B1:FC:09:6A:FE from 98:4F:EE:04:1A:8C (data size 44) ...
44 bytes from E8:B1:FC:09:6A:FE id 0 time 29.50ms
44 bytes from E8:B1:FC:09:6A:FE id 1 time 29.18ms
44 bytes from E8:B1:FC:09:6A:FE id 2 time 13.04ms
44 bytes from E8:B1:FC:09:6A:FE id 3 time 29.45ms
^C4 sent, 4 received, 0% loss
root@edison:~# 
```

# SDPTool

@ Linux Based Laptop

```sh
root@edison:~# sdptool browse  E8:B1:FC:09:6A:FE
```

```
Browsing E8:B1:FC:09:6A:FE ...
Service Name: SIM Access Server
Service RecHandle: 0x10000
Service Class ID List:
  "SIM Access" (0x112d)
  "Generic Telephony" (0x1204)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 8
Profile Descriptor List:
  "SIM Access" (0x112d)
    Version: 0x0101

Service Name: Headset Audio Gateway
Service RecHandle: 0x10001
Service Class ID List:
  "Headset Audio Gateway" (0x1112)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 12
Profile Descriptor List:
  "Headset" (0x1108)
    Version: 0x0102

Service Name: Hands-Free Audio Gateway
Service RecHandle: 0x10002
Service Class ID List:
  "Handsfree Audio Gateway" (0x111f)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 13
Profile Descriptor List:
  "Handsfree" (0x111e)  
    Version: 0x0105

Service Name: Hands-Free
Service RecHandle: 0x10003
Service Class ID List:
  "Handsfree" (0x111e)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 7
Profile Descriptor List:
  "Handsfree" (0x111e)
    Version: 0x0105

Service Name: AVRCP TG
Service RecHandle: 0x10004
Service Class ID List:
  "AV Remote Target" (0x110c)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 23
  "AVCTP" (0x0017)
    uint16: 0x0103
Profile Descriptor List:
  "AV Remote" (0x110e)
    Version: 0x0104

Service Name: AVRCP CT
Service RecHandle: 0x10005
Service Class ID List:
  "AV Remote" (0x110e)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 23
  "AVCTP" (0x0017)
    uint16: 0x0103
Profile Descriptor List:
  "AV Remote" (0x110e)
    Version: 0x0100

Service Name: Audio Source
Service RecHandle: 0x10006
Service Class ID List:
  "Audio Source" (0x110a)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 25
  "AVDTP" (0x0019)
    uint16: 0x0102
Profile Descriptor List:
  "Advanced Audio" (0x110d)
    Version: 0x0102

Service Name: Audio Sink
Service RecHandle: 0x10007
Service Class ID List:
  "Audio Sink" (0x110b)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 25
  "AVDTP" (0x0019)
    uint16: 0x0102
Profile Descriptor List:
  "Advanced Audio" (0x110d)
    Version: 0x0102
```

@ Arduino Based Board

```sh
root@edison:~# sdptool browse 98:4F:EE:0F:2B:E0 
Failed to connect to SDP server on 98:4F:EE:0F:2B:E0: Host is down
root@edison:~# 
```

# GattTool

- [Using the Generic Attribute Profile (GATT) in Bluetooth* Low Energy with your Intel® Edison Board](https://software.intel.com/en-us/articles/using-the-generic-attribute-profile-gatt-in-bluetooth-low-energy-with-your-intel-edison)

```sh
root@edison: cd ~
root@edison: wget 	
https://www.kernel.org/pub/linux/bluetooth/bluez-5.24.tar.xz –	no-check-certificate
root@edison: tar -xf bluez-5.24.tar.xz
root@edison: cd bluez-5.24
root@edison: ./configure --disable-systemd –disable-udev
root@edison: make
root@edison: make install

To be able to launch gatttool from anywhere add it to the path:

root@edison: export PATH=$PATH:~/bluez-5.24/attrib/
```

# BTMon

```sh
root@edison:~# btmon 
Bluetooth monitor ver 5.37
= New Index: 98:4F:EE:04:1A:8C (BR/EDR,UART,hci0)               [hci0] 0.908322
```

```sh
root@edison:~# hcitool lescan
```