Protocols
==



### Mosquitto

> Mosquitto is an open source (BSD licensed) message broker that implements the MQ Telemetry Transport protocol versions 3.1 and 3.1.1. MQTT provides a lightweight method of carrying out messaging using a publish/subscribe model.

## MQTT

> MQTT (Message Queue Telemetry Transport) is a light-weight protocol used for Machine to Machine (M2M) communication. MQTT used a publish/subscribe message forwarding model built on top of TCP/IP protocol, according to this protocol architecture, it's possible to have as many subscribers we want without limit, but only one publisher.

>MQTT (a.k.a. mosquitto) is perfect for mobile and embedded devices because of its lightweight (in processing, memory management and bandwidth) messaging protocol. 

> For this protocol, notice that it lacks of encryption in its base, otherwise it would add an important overhead to the connection. Security at the application level requires a lot of work.

[Mosquitto Homepage](http://mosquitto.org/)


#### Mosquitto Intel® Edison Setup

[Building and running Mosquitto MQTT on Intel Edison](https://software.intel.com/en-us/blogs/2015/02/20/building-and-running-mosquitto-mqtt-on-intel-edison)


#### Mosquitto Intel® Galileo Setup

    root@galileo:~# wget http://mosquitto.org/files/source/mosquitto-1.3.5.tar.gz
    root@galileo:~# tar xvf mosquitto-1.3.5.tar.gz
    root@galileo:~# cd mosquitto-1.3.5
    root@galileo:~# make -j3 WITH_SRV=no
    root@galileo:~# adduser mosquitto
    root@galileo:~# cd test/broker
    root@galileo:~# make -j3 test
    root@galileo:~# cd ../../
    root@galileo:~# cp client/mosquitto_pub /usr/bin
    root@galileo:~# cp client/mosquitto_sub /usr/bin
    root@galileo:~# cp lib/libmosquitto.so.1 /usr/lib
    root@galileo:~# cp src/mosquitto /usr/bin

#### Mosquitto Applications

    root@platform:~# mosquitto
    root@platform:~# mosquitto_sub
    root@platform:~# mosquitto_pub

#### Mosquitto Demo Temperature Gauge

Go to http://test.mosquitto.org/gauge/ and execute

    root@platform:~# mosquitto_pub -h test.mosquitto.org -t temp/random -m 23.0

####  Mosquitto MQTT Server/Broker

As subscriber

    root@galileo:~# mosquitto_sub -h test.mosquitto.org -p 1883 -t workshop/galileo
    root@edison:~# mosquitto_sub -h test.mosquitto.org -p 1883 -t workshop/edison

As publisher

    root@galileo:~# mosquitto_pub -h test.mosquitto.org -p 1883 -t workshop/galileo -m "Hello Galileo Operators!"
    root@edison:~# mosquitto_pub -h test.mosquitto.org -p 1883 -t workshop/edison -m "Hello Edison Operators!"

As subscriber

    root@platform:~# mosquitto_sub -h test.mosquitto.org -p 1883 -t workshop/all

As publisher

    root@platform:~# mosquitto_pub -h test.mosquitto.org -p 1883 -t workshop/all -m "Hello All Operators!"

See output for the following command

    root@platform:~# mosquitto_sub -h test.mosquitto.org -t "#" -v

## Constrained Application Protocol (CoAP)

> Constrained Application Protocol (CoAP) is a software protocol intended to be used in very simple electronics devices that allows them to communicate interactively over the Internet. It is particularly targeted for small low power sensors, switches, valves and similar components that need to be controlled or supervised remotely, through standard Internet networks ... *From Wikipedia, the free encyclopedia*

>CoAp has a request/response model protocol, clients can make GET, PUT, POST and DELETE requests to resources. Please notice that CoAp does not have SSL/TLS ecryption isn't available over UDP, CoAP makes use of DTLS (Datagram Transport Layer Security). The default level of encryption is equivalent to a 3,072-bit RSA key. Also, CoAp lacks of a publish-subscribe message queue.


https://www.artik.io/blog/2015/iot-101-networks

## 6lowpan

Tbd

## RPL

Tbd

## LoraWAN

- https://www.lora-alliance.org/
