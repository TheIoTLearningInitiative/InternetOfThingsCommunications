# Mosquitto

> Mosquitto is an open source (BSD licensed) message broker that implements the MQ Telemetry Transport protocol versions 3.1 and 3.1.1. MQTT provides a lightweight method of carrying out messaging using a publish/subscribe model.

>MQTT (a.k.a. mosquitto) is perfect for mobile and embedded devices because of its lightweight (in processing, memory management and bandwidth) messaging protocol. 

> For this protocol, notice that it lacks of encryption in its base, otherwise it would add an important overhead to the connection. Security at the application level requires a lot of work.

[Mosquitto Homepage](http://mosquitto.org/)

### Mosquitto Intel® Edison Setup

- [Building and running Mosquitto MQTT on Intel Edison](https://software.intel.com/en-us/blogs/2015/02/20/building-and-running-mosquitto-mqtt-on-intel-edison)
- [Connecting Sensor Networks and Devices to the Cloud in just minutes: Solution Brief](https://software.intel.com/sites/default/files/managed/52/10/IBM_Connecting_Sensor_Networks_and_Devices_Cloud_Minutes_Rev1_2.pdf)

### Mosquitto Intel® Galileo Setup

```sh
    root@platform:~# wget http://mosquitto.org/files/source/mosquitto-1.3.5.tar.gz
    root@platform:~# tar xvf mosquitto-1.3.5.tar.gz
    root@platform:~# cd mosquitto-1.3.5
    root@platform:~# make -j3 WITH_SRV=no
    root@platform:~# adduser mosquitto
    root@platform:~# cd test/broker
    root@platform:~# make -j3 test
    root@platform:~# cd ../../
    root@platform:~# cp client/mosquitto_pub /usr/bin
    root@platform:~# cp client/mosquitto_sub /usr/bin
    root@platform:~# cp lib/libmosquitto.so.1 /usr/lib
    root@platform:~# cp src/mosquitto /usr/bin
```

### Mosquitto Applications

```sh
    root@platform:~# mosquitto
    root@platform:~# mosquitto_sub
    root@platform:~# mosquitto_pub
```

### Mosquitto Demo Temperature Gauge

Go to http://test.mosquitto.org/gauge/ and execute

```sh
    root@platform:~# mosquitto_pub -h test.mosquitto.org -t temp/random -m 23.0
```
###  Mosquitto MQTT Server/Broker

As subscriber

```sh
    root@platform:~# mosquitto_sub -h test.mosquitto.org -p 1883 -t workshop/galileo
    root@platform:~# mosquitto_sub -h test.mosquitto.org -p 1883 -t workshop/edison
```

As publisher

```sh
    root@platform:~# mosquitto_pub -h test.mosquitto.org -p 1883 -t workshop/galileo -m "Hello Galileo Operators!"
    root@platform:~# mosquitto_pub -h test.mosquitto.org -p 1883 -t workshop/edison -m "Hello Edison Operators!"
```

As subscriber

```sh
    root@platform:~# mosquitto_sub -h test.mosquitto.org -p 1883 -t workshop/all
```

As publisher

```sh
    root@platform:~# mosquitto_pub -h test.mosquitto.org -p 1883 -t workshop/all -m "Hello All Operators!"
```

See output for the following command

```sh
    root@platform:~# mosquitto_sub -h test.mosquitto.org -t "#" -v
```
