# GATTTool

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

