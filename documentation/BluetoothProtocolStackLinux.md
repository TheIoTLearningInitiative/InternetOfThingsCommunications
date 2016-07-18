# Linux

- [Man Pages Name sdptool -- Control and interrogate SDP servers](http://linux.die.net/man/1/sdptool)
- [An Introduction to Bluetooth Programming by Albert Huang](https://people.csail.mit.edu/albert/bluez-intro/index.html)


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