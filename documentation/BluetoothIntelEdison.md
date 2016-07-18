# Intel Edison

- [Intel® Edison Bluetooth Guide](http://www.intel.com/support/edison/sb/CS-035381.htm)
- [Intel® Edison SPP](https://software.intel.com/en-us/articles/connecting-the-intel-edison-board-to-your-android-phone-with-serial-port-profile-spp)

# Setup

```sh
root@edison:~# opkg install bluez5 bluez-hcidump
Package bluez5 (5.37-r0) installed in root is up to date.
Package bluez5 (5.37-r0) installed in root is up to date.
root@edison:~# 
```

# Pairing Devices

```sh
root@edison:~# rfkill unblock bluetooth
root@edison:~# hciconfig hci0 up
root@edison:~# bluetoothctl
[NEW] Controller 98:4F:EE:04:1A:8C MyEdison [default]
[NEW] Device 98:4F:EE:06:1B:99 edison
[NEW] Device 2C:D0:5A:80:7A:44 AARCEMOR-MOBL3
[NEW] Device 98:4F:EE:0F:2B:E0 LED
[NEW] Device E8:B1:FC:09:6A:FE ubuntu-gnome-0
[NEW] Device 40:78:6A:26:4A:C2 XT1008
[bluetooth]# 
````

# RFComm

```sh
    root@galileo:~# rfkill unblock bluetooth
    root@galileo:~# bluetoothctl
    [bluetooth]# scan on
    [bluetooth]# scan off
    [bluetooth]# pair 40:78:6A:26:4A:C2
    [bluetooth]# connect 40:78:6A:26:4A:C2
    [bluetooth]# paired-devices
    [bluetooth]# info 40:78:6A:26:4A:C2
    [bluetooth]# exit
    root@edison:~# rfcomm bind - 40:78:6A:26:4A:C2 1
    root@edison:~# ls /dev/rfcomm0
```

# BlueTooth Headsets

```sh
    root@edison:~# rfkill unblock bluetooth
    root@edison:~# bluetoothctl
    root@edison:~# scan on
    root@edison:~# pair 40:78:6A:26:4A:C1
    root@edison:~# connect 40:78:6A:26:4A:C1
    root@edison:~# quit
    root@edison:~# pactl list sinks
    root@edison:~# pactl set-default-sink bluez_sink.40_78_6A_26_4A_C1
    root@edison:~# gst-launch-1.0 filesrc location=sample.wav ! waveparse ! pulsesink
    root@edison:~# paired-devices
    root@edison:~# remove 40:78:6A:26:4A:C1
```
