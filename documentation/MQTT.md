# MQ Telemetry Transport

> MQTT is a light-weight protocol used for Machine to Machine (M2M) communication. MQTT used a publish/subscribe message forwarding model built on top of TCP/IP protocol.

> MQTT is a machine-to-machine (M2M)/"Internet of Things" connectivity protocol. It was designed as an extremely lightweight publish/subscribe messaging transport. It is useful for connections with remote locations where a small code footprint is required and/or network bandwidth is at a premium.

- [MQTT Homepage](http://mqtt.org/)
- [MQTT Protocol Specification](http://www.ibm.com/developerworks/library/ws-mqtt/)
- [HiveMQ MQTT Essentials](http://www.hivemq.com/mqtt-essentials/)
- [HiveMQ MQTT Essentials: Part 1 – Introducing MQTT](http://www.hivemq.com/blog/mqtt-essentials-part-1-introducing-mqtt)
- [HiveMQ MQTT Essentials Wrap-Up](http://www.hivemq.com/blog/mqtt-essentials-wrap-up)
- [Minimal MQTT: Networked Nodes](http://hackaday.com/2016/05/17/minimal-mqtt-networked-nodes/)
- [Working with Bottlenecks: CoAP and MQTT](http://learninginternetofthings.com/bottlenecks-coap-mqtt/)
- [MQTT is the de-facto standard and ISO standard for messaging protocols](https://developer.ibm.com/dwblog/mqtt-de-facto-standard-iso-messaging/)

Core Messages

- Connect
- Disconnect
- Publish
- Subscribe
- Unsubscribe

Quality of Services

- 0, 1, 2

[HiveMQ MQTT Essentials Part 6: Quality of Service 0, 1 & 2](http://www.hivemq.com/mqtt-essentials-part-6-mqtt-quality-of-service-levels/)

# Server Implementations

- IBM MQ
- IBM Microbroker
- RSMB
- Mosquitto
- MQTT.js
- Apache ActiveMQ
- RabbitMQ
- [Adafruit MQTT API](https://learn.adafruit.com/adafruit-io/mqtt-api)
- [Microsoft Azure](http://iotmakerdendashboard.azurewebsites.net/install/publish.htm)

# Clients

> We’re very excited to announce the MQTT Client Library Encyclopedia [HiveMQ MQTT Client Library Encyclopedia](http://www.hivemq.com/mqtt-client-library-encyclopedia/)

- C/C++/C#
- Java
- Perl
- Python
- PHP
- Rex
- Ruby
- Arduino

# Brokers

- [Cloud MQTT Hosted broker for the Internet of Things](https://www.cloudmqtt.com/)
- [Mosquitto](http://test.mosquitto.org/)
- [Eclipse MQTT](http://iot.eclipse.org/getting-started#tutorials)
- [MQTT Dashboard](broker.mqtt-dashboard.com)

# Mosquitto

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


