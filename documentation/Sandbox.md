SandBox
==

Band X Available for Agro

- [Avoid the Silos and Help Build the True Internet of Things](http://events.linuxfoundation.org/sites/events/files/slides/Avoid%20the%20Silos%20and%20Build%20the%20True%20Internet%20of%20Things.pdf)
- [A Resource Framework for the Internet of Things] (http://events.linuxfoundation.org/sites/events/files/slides/Resource%20Framework%20for%20the%20IoT%20San%20Diego%20Final.pdf)

Basics of IoT Communication from [Architecting the Internet of Things by Microsoft @ TechEd North America](https://www.youtube.com/watch?v=ZMHQu_X0Ijk)

- Telemetry: Information flowing from a device to other systems for conveying status of device and environment
- Inquiries: Requests from devices looking to gather required information or to initiate activities, I Am Ok!
- Commands: Command from other systems to a device or a group of devices to perform specific activities
- Notifications: Information flowing from other systems to a device (group) for conveying status changes

> A service-oriented architecture (SOA) is an architectural pattern in computer software design in which application components provide services to other components via a communications protocol, typically over a network. The principles of service-orientation are independent of any vendor, product or technology. [Wikipedia](https://en.wikipedia.org/wiki/Service-oriented_architecture)


## M2M

Definition to provide a background, as an antecesor of IoT Comms

## OSI Model



## TCP/IP

## Open Geospatial Consortium

- [OGC (Open Geospatial Consortium) SensorThings API ](http://ogc-iot.github.io/ogc-iot-api/)


- Kernel
  - IPv4
  - IPv6
  - L2CAP
  - BLE
  - 6LowPAN
  - 802.15.4
  - Ethernet
  - WiFi
  - UDP
  - TCP
  - MPTCP

Middleware
 - BlueZ Bluetooth Stack
 - ConnMann IP Networking
 - iwd WiFi
 - NearD NFC
 - Ofono Telephony, 3G, LTE

Frameworks
 - IoTivity OIC
 - cURL HTTP Client
 - microhttpd HTTP Server
 - mosquitto MQTT

Industrial
 - CAN bus
 - EtherCAT
 - Profinet


  


# The Things Network

> Unleashing the Internet of Things. We are on a mission to build a global open crowdsourced Internet of Things data network. [Homepage](http://preview.thethingsnetwork.org/)

- [The Things Network Github](https://github.com/TheThingsNetwork/)

https://developer.ibm.com/recipes/tutorials/integrating-watson-iot-platform-with-message-hubkafka/
This section contains all data that is missing. You might find it not structed, that is ok, important thing is not to forget about it.

http://ardiri.com/blog/rf_433mhz_radio_communication_with_an_arduino

## Z-Wave

Aeon Labs DSA02203-ZWUS Z-Wave Z-Stick Series 2*
http://flows.nodered.org/flow/b993a7bd7a2832edb23a
https://thefrinkiac7.wordpress.com/node-red/node-red-and-zwave-on-raspberry-pi2/

## ZigBee

Found under Linux Embeeded Application DEvelopment

## ModBus

https://software.intel.com/en-us/blogs/2015/11/27/modbus-on-intelr-edison/

## Protocols

REST

## Terminology

### MQ Publish/Subscribe Model

[IBM Interconnect 2015 - Publish/subscribe in an IBM MQ network ](https://www.youtube.com/watch?v=iBq3oUBZ-9s)

- Make it extendable
- Rapidly changing set of topic strings
- Avoid excessively wide or deep dynamic topic tress

Components

- Topic String
- Topic Object
- Object Attributes
- Object Security
- Types of Subscriptions

Publications

- Always Succesful? Might, if Durable and Persistent

- [IBM Interconnect 2015 - Publish/subscribe in an IBM MQ network ](https://www.youtube.com/watch?v=iBq3oUBZ-9s)

## Workshop

Big time to work on for

- REST create an example
- MQTT using IBM Bluemix
- AMQP using IBM MQ Light
- Z-Wave using [Post Z-Wave Data to Node Red](https://www.ibm.com/developerworks/community/blogs/cee6c09c-a315-4b04-ad14-57d6a60fa8bb/entry/post_z_wave_data_to_node_red?lang=en)