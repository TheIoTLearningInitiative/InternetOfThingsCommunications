# Protocols

- [IoT request response protocol](http://codesanswer.com/question/261384-iot-request-response-protocol)
- [The Internet of Things: Key Applications and Protocols](http://techbus.safaribooksonline.com/book/information-technology-and-software-development/9781119994350)
- [Sparkfun Exploring the Protocols of IoT](https://www.sparkfun.com/news/1705)
- [11 Internet of Things (IoT) Protocols You Need to Know About](http://www.rs-online.com/designspark/electronics/knowledge-item/eleven-internet-of-things-iot-protocols-you-need-to-know-about)

## RPL

Tbd

## LoraWAN

- https://www.lora-alliance.org/


Protocols
==
> In telecommunications, a communications protocol is a system of rules that allow two or more entities of a communications system to transmit information via any kind of variation of a physical quantity. These are the rules or standard that defines the syntax, semantics and synchronization of communication and possible error recovery methods. Protocols may be implemented by hardware, software, or a combination of both. [Wikipedia](https://en.wikipedia.org/wiki/Communications_protocol)

- [Postscapes Internet of Things Protocols & Standards](http://postscapes.com/internet-of-things-protocols)

## IPv6

> Internet Protocol version 6 (IPv6) is the most recent version of the Internet Protocol (IP), the communications protocol that provides an identification and location system for computers on networks and routes traffic across the Internet. IPv6 was developed by the Internet Engineering Task Force (IETF) to deal with the long-anticipated problem of IPv4 address exhaustion. IPv6 is intended to replace IPv4. Wikipedia

- [IPv6 Wikipedia](https://en.wikipedia.org/wiki/IPv6)

## Ajax, Web services, RESTful communication protocols

> These sit on top of HTTP, thus suffering from the same limitations as HTTP. Many of these protocols also require extensive processing and have a huge code size footprint. Many service providers promote the use of these protocols since their backend infrastructure is based on standard web servers that cannot handle any other type of protocol than HTTP.

## RESTful API (Representational State Transfer)

> In computing, representational state transfer (REST) is the software architectural style of the World Wide Web. REST's coordinated set of constraints, applied to the design of components in a distributed hypermedia system, can lead to a higher-performing and more maintainable software architecture. [Wikipedia](https://en.wikipedia.org/wiki/Representational_state_transfer)

> To the extent that systems conform to the constraints of REST they can be called RESTful. RESTful systems typically, but not always, communicate over Hypertext Transfer Protocol (HTTP) with the same HTTP verbs (GET, POST, PUT, DELETE, etc.) that web browsers use to retrieve web pages and to send data to remote servers.[4] REST systems interface with external systems as web resources identified by Uniform Resource Identifiers (URIs), for example /people/tom, which can be operated upon using standard verbs such as DELETE /people/tom. [Wikipedia](https://en.wikipedia.org/wiki/Representational_state_transfer) 

- [Learn REST: A Tutorial](http://rest.elkstein.org/)

### API Creation

> Creating and exposing APIs allows your web application to interact with other applications through machine-to-machine communication. API creation frameworks... [FullStackPython](http://www.fullstackpython.com/api-creation.html)

### Flask

> Flask is a microframework for Python based on Werkzeug, Jinja 2 and good intentions. [Flask Homepage](http://flask.pocoo.org/)

> It’s time to write your first REST API. This guide assumes you have a working understanding of Flask, and that you have already installed both Flask and Flask-RESTful. [Here]([http://flask-restful-cn.readthedocs.org/en/0.3.4/quickstart.html)

[Browsable Web APIs for Flask](http://www.flaskapi.org/)

```sh
    root@board:~# pip install Flask
    Downloading/unpacking Flask
      Downloading Flask-0.10.1.tar.gz (544kB): 544kB downloaded
    Installing collected packages: Flask
    Successfully installed Flask
    Cleaning up...
    root@board:~# 
```

### Flask-RESTful

> Flask-RESTful is an extension for Flask that adds support for quickly building REST APIs. It is a lightweight abstraction that works with your existing ORM/libraries. Flask-RESTful encourages best practices with minimal setup. If you are familiar with Flask, Flask-RESTful should be easy to pick up. [Flask-RESTful Documentation](http://flask-restful.readthedocs.org/en/latest/index.html)

```sh
    root@board:~# pip install flask-restful
    Downloading/unpacking flask-restful
      Downloading Flask-RESTful-0.3.5.tar.gz (102kB): 102kB downloaded
    Downloading/unpacking aniso8601>=0.82 (from flask-restful)
      Downloading aniso8601-1.1.0.tar.gz (49kB): 49kB downloaded
    Downloading/unpacking python-dateutil (from aniso8601>=0.82->flask-restful)
      Downloading python-dateutil-2.5.1.tar.gz (235kB): 235kB downloaded
    Installing collected packages: flask-restful, aniso8601, python-dateutil
    Successfully installed flask-restful aniso8601 python-dateutil
    Cleaning up...
    root@board:~# 
```

### Project

```sh
    root@board:~# vi mainflask.py
```

```python
#!/usr/bin/python
from flask import Flask
from flask_restful import Api, Resource

app = Flask(__name__)
api = Api(app)

class Network(Resource):
    def get(self):
        data = 'Network Data'
        return data

api.add_resource(Network, '/network')

if __name__ == '__main__':
    app.run(debug=True)
```

```sh
    root@board:~# python mainflask.py
     * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
     * Restarting with stat
     * Debugger is active!
     * Debugger pin code: 331-202-890
```

Connect to your boardipaddress:5000 in a web browser

```sh
    127.0.0.1 - - [28/Dec/2015 15:07:38] "GET /network HTTP/1.1" 200 -
    127.0.0.1 - - [28/Dec/2015 15:07:40] "GET /network HTTP/1.1" 200 -
```
## MQTT

> MQTT is a light-weight protocol used for Machine to Machine (M2M) communication. MQTT used a publish/subscribe message forwarding model built on top of TCP/IP protocol.

> MQTT is a machine-to-machine (M2M)/"Internet of Things" connectivity protocol. It was designed as an extremely lightweight publish/subscribe messaging transport. It is useful for connections with remote locations where a small code footprint is required and/or network bandwidth is at a premium.

- [MQTT Homepage](http://mqtt.org/)
- [MQTT Protocol Specification](http://www.ibm.com/developerworks/library/ws-mqtt/)
- [HiveMQ MQTT Essentials: Part 1 – Introducing MQTT](http://www.hivemq.com/blog/mqtt-essentials-part-1-introducing-mqtt)
- [HiveMQ MQTT Essentials Wrap-Up](http://www.hivemq.com/blog/mqtt-essentials-wrap-up)

### Features

Core Messages

- Connect
- Disconnect
- Publish
- Subscribe
- Unsubscribe

Quality of Services

- 0, 1, 2

[HiveMQ MQTT Essentials Part 6: Quality of Service 0, 1 & 2](http://www.hivemq.com/mqtt-essentials-part-6-mqtt-quality-of-service-levels/)

### Server Implementations

- IBM MQ
- IBM Microbroker
- RSMB
- Mosquitto
- MQTT.js
- Apache ActiveMQ
- RabbitMQ
- [Adafruit MQTT API](https://learn.adafruit.com/adafruit-io/mqtt-api)

### Clients

- C/C++/C#
- Java
- Perl
- Python
- PHP
- Rex
- Ruby
- Arduino

#### Mosquitto

> Mosquitto is an open source (BSD licensed) message broker that implements the MQ Telemetry Transport protocol versions 3.1 and 3.1.1. MQTT provides a lightweight method of carrying out messaging using a publish/subscribe model.

[Mosquitto Homepage](http://mosquitto.org/)


##### Mosquitto Intel® Edison Setup

We should have all Mosquitto MQTT tools available in latest version of Linux Yocto based version

- [Building and running Mosquitto MQTT on Intel Edison Old Version](https://software.intel.com/en-us/blogs/2015/02/20/building-and-running-mosquitto-mqtt-on-intel-edison)
- [CONNECTING SENSOR NETWORKS AND DEVICES TO THE CLOUD IN JUST MINUTES: SOLUTION BRIEF](https://software.intel.com/sites/default/files/managed/52/10/IBM_Connecting_Sensor_Networks_and_Devices_Cloud_Minutes_Rev1_2.pdf)

##### Mosquitto Intel® Galileo Setup

```sh
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
```

##### Mosquitto Applications

```sh
    root@platform:~# mosquitto
    root@platform:~# mosquitto_sub
    root@platform:~# mosquitto_pub
```

##### Mosquitto Demo Temperature Gauge

Go to [http://test.mosquitto.org/gauge/](http://test.mosquitto.org/gauge/) and execute

```sh
    root@platform:~# mosquitto_pub -h test.mosquitto.org -t temp/random -m 23.0
```

#####  Mosquitto MQTT Server/Broker

As subscribers

```sh
    root@board:~# mosquitto_sub -h test.mosquitto.org -p 1883 -t IoT101/#
```

As publishers

```sh
    root@board:~# mosquitto_pub -h test.mosquitto.org -p 1883 -t IoT101/all -m "Hello All Operators!"
```

See output from the following command

```sh
    root@board:~# mosquitto_sub -h test.mosquitto.org -t "#" -v
```

### Project

> Eclipse Paho MQTT Python client library, which implements versions 3.1 and 3.1.1 of the MQTT protocol.

[Paho Mqtt](https://pypi.python.org/pypi/paho-mqtt)

Publish system-wide network I/O statistics through MQTT Protocol using test.mosquitto.org server under "IoT101" topic

```sh
    root@board:~# vi main.py
```

```python
#!/usr/bin/python

import paho.mqtt.client as paho
import psutil
import signal
import sys
import time

from threading import Thread

def interruptHandler(signal, frame):
    sys.exit(0)

def on_publish(mosq, obj, msg):
    pass

def dataNetwork():
    netdata = psutil.net_io_counters()
    return netdata.packets_sent + netdata.packets_recv

def dataNetworkHandler():
    idDevice = "ThisDevice"
    mqttclient = paho.Client()
    mqttclient.on_publish = on_publish
    mqttclient.connect("test.mosquitto.org", 1883, 60)
    while True:
        packets = dataNetwork()
        message = idDevice + " " + str(packets)
        print "MQTT dataNetworkHandler " + message
        mqttclient.publish("IoT101/Network", message)
        time.sleep(1)

if __name__ == '__main__':

    signal.signal(signal.SIGINT, interruptHandler)

    threadx = Thread(target=dataNetworkHandler)
    threadx.start()

    while True:
        print "Hello Internet of Things 101"
        time.sleep(5)


# End of File
```

```sh
    root@board:~# python main.py
```

Listen to those events with mosquitto_pub app or any mqtt cellphone application using a test.mosquitto.org server susbcribing to "IoT101/#"

```sh
    root@board:~# mosquitto_sub -h test.mosquitto.org -p 1883 -t IoT101/#
```
Implement a threaded subscription function through MQTT Protocol using a test.mosquitto.org server under "IoT101/Message" topic

```sh
    root@board:~# vi main.py
```

```python
#!/usr/bin/python

import paho.mqtt.client as paho
import psutil
import signal
import sys
import time

from threading import Thread

def interruptHandler(signal, frame):
    sys.exit(0)

def on_publish(mosq, obj, msg):
    pass

def dataNetwork():
    netdata = psutil.net_io_counters()
    return netdata.packets_sent + netdata.packets_recv

def dataNetworkHandler():
    idDevice = "ThisDevice"
    mqttclient = paho.Client()
    mqttclient.on_publish = on_publish
    mqttclient.connect("test.mosquitto.org", 1883, 60)
    while True:
        packets = dataNetwork()
        message = idDevice + " " + str(packets)
        print "dataNetworkHandler " + message
        mqttclient.publish("IoT101/Network", message)
        time.sleep(1)

def on_message(mosq, obj, msg):
    print "MQTT dataMessageHandler %s %s" % (msg.topic, msg.payload)

def dataMessageHandler():
    mqttclient = paho.Client()
    mqttclient.on_message = on_message
    mqttclient.connect("test.mosquitto.org", 1883, 60)
    mqttclient.subscribe("IoT101/Message", 0)
    while mqttclient.loop() == 0:
        pass

if __name__ == '__main__':

    signal.signal(signal.SIGINT, interruptHandler)

    threadx = Thread(target=dataNetworkHandler)
    threadx.start()

    threadx = Thread(target=dataMessageHandler)
    threadx.start()

    while True:
        print "Hello Internet of Things 101"
        time.sleep(5)


# End of File
```

```sh
    root@board:~# python main.py
```

Confirm you are receiving those events publishing from another device

```sh
    root@board:~# mosquitto_pub -h test.mosquitto.org -p 1883 -t IoT101/Message -m Hi
```

## Advanced Message Queuing Protocol

> The Advanced Message Queuing Protocol (AMQP) is an open standard for passing business messages between applications or organizations.  It connects systems, feeds business processes with the information they need and reliably transmits onward the instructions that achieve their goals.

- [AMQP Homepage](https://www.amqp.org/)
- [Pika](https://github.com/pika/pika)
- [Low-level AMQP client for Python](https://pypi.python.org/pypi/amqp/1.4.8)
- [IBM MQ Light](https://developer.ibm.com/messaging/mq-light/)
- [MQ Light and AMQP (Advanced Message Queuing Protocol)](https://developer.ibm.com/messaging/mq-light/docs/amqp/)

## Weave

> Weave* is a communications protocol that supports discovery, provisioning, and authentication so that devices can connect and interact with one another, the Internet, and your mobile platforms. The Weave protocol helps IoT developers extend the reach of mobile apps to the physical world. Developers can build one app to control multiple devices that leverage Google services.

> Weave is a communications platform for IoT devices that enables device setup, phone-to-device-to-cloud communication, and user interaction from mobile devices and the web.

- [Weave Homepage](https://developers.google.com/weave/)

## Constrained Application Protocol (CoAP)

> Constrained Application Protocol (CoAP) is a software protocol intended to be used in very simple electronics devices that allows them to communicate interactively over the Internet. It is particularly targeted for small low power sensors, switches, valves and similar components that need to be controlled or supervised remotely, through standard Internet networks ... *From Wikipedia, the free encyclopedia*

## AllJoyn

> A persistent publish/subscribe solution promoted by Qualcomm. This protocol has the limitation of being mainly targeted towards home electronics. This protocol includes code for marshalling and unmarshalling (encode/decode) data and suffers from the same size and proxy problems as MQTT

## XMPP

> An open source persistent publish/subscribe protocol that can also be tunneled over HTTP. Data is encoded in XML, thus it includes a huge code size footprint for the device

## 6LoWPAN

> 6LoWPAN is an acronym of IPv6 over Low power Wireless Personal Area Networks. 6LoWPAN is the name of a concluded working group in the Internet area of the IETF. Wikipedia

> The 6LoWPAN concept originated from the idea that "the Internet Protocol could and should be applied even to the smallest devices" and that low-power devices with limited processing capabilities should be able to participate in the Internet of Things. Wikipedia

[6LoWPAN Interoperability](http://tools.ietf.org/html/draft-daniel-6lowpan-interoperability-01)

## ModBus

> Modbus is a serial communications protocol originally published by Modicon (now Schneider Electric) in 1979 for use with its programmable logic controllers (PLCs). Simple and robust, it has since become a de facto standard communication protocol, and it is now a commonly available means of connecting industrial electronic devices. Wikipedia

> Since Modbus protocol is just a messaging structure, it is independent of the underlying physical layer. It is traditionally implemented using RS232, RS422, or RS485. The Request. The function code in the request tells the addressed slave device what kind of action to perform.

- [ModBus on Intel Edison](https://software.intel.com/en-us/blogs/2015/11/27/modbus-on-intelr-edison)
- [ModBus on Intel Galileo](https://www.cooking-hacks.com/documentation/tutorials/modbus-module-shield-tutorial-for-arduino-raspberry-pi-intel-galileo/)

## Others

- SOAP, UPnP, RPL
- VSCP (Very Simple Control Protocol) - the leading m2m and telematics protocol


