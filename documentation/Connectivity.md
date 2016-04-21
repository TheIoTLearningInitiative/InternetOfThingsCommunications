# Connectivity

> One of the strengths of the Internet of Things (IoT) is its capability to network things. As Greenough and Camhi say in [The Internet Of Things 2015 Report](http://www.businessinsider.com/internet-of-things-2015-forecasts-of-the-industrial-iot-connected-home-and-more-2015-10) of Business Insider, IoT is and will continue to change the way business, governments, and consumers are interacting with the world around us. Because of this main purpose to connect people and things in general, the most important thing is actually connectivity.

> Forbes reported that during 2015 4,800 connected end points are added every minute, and a prediction of [McKinsey & Company](http://www.mckinsey.com/insights/high_tech_telecoms_internet/the_internet_of_things_sizing_up_the_opportunity) forecasts 30 billion IoT objects connected by 2020.

![IoT Prediction](IoTPrediction2.PNG)

> Nowadays, we cannot predict exactly how communication protocols will evolve, but we can breakdown wireless communication protocols in 6 standards:

1. Satellite
2. WiFi
3. Radio Frequency (RF)
4. RFID
5. Bluetooth
6. NFC

## Satellite
> 

## Technologies

### Low Range

3G, GPRS, LoRa, Sigfox, 868 MHz, 900 MHz

### Medium Range

ZigBee, 802.15.4

### Short Range

WiFi, RFID, NFC, BlueTooth 4.0


Connectivity
==

> Artik.Io This is the first in a series of tutorials we’re calling IoT 101... [Artik IoT 101 Connectivity](https://www.artik.io/blog/2015/iot-101-connectivity)

> In this installment of our IoT 101 series we discuss how to select network protocols based on the way you want to interact with your IoT... [Artik.Io IoT 101 Networks](https://www.artik.io/blog/2015/iot-101-networks) 

## Telephony

3G, 4G, LTE

## WiFi

- IEEE 802.11
- IEEE 802.11b
- IEEE 802.11g
- IEEE 802.11n

- [Intel® Edison Wi-Fi Guide](https://software.intel.com/en-us/articles/intel-edison-wi-fi-guide)
- [Lowest Power WiFi in the World: Atmel | SMART SAM W25 Wi-Fi for IoT with ARM Cortex-M0+](https://www.youtube.com/watch?v=pOFU0KCly80)

### WiFi HaLow

> Wi-Fi HaLow operates in frequency bands below one gigahertz, offering longer range, lower power connectivity

- [Wi-Fi Alliance® introduces low power, long range Wi-Fi HaLow™](https://www.wi-fi.org/news-events/newsroom/wi-fi-alliance-introduces-low-power-long-range-wi-fi-halow)

## Wi-Gig

> The WiGig specification allows devices to communicate without wires at multi-gigabit speeds. It enables high performance wireless data, display and audio applications that supplement the capabilities of previous wireless LAN devices. Wikipedia

- [Wireless Gigabit Alliance Wikipedia](https://en.wikipedia.org/wiki/Wireless_Gigabit_Alliance)

## Bluetooth

> Bluetooth is a wireless technology standard for exchanging data over short distances (using short-wavelength UHF radio waves in the ISM band from 2.4 to 2.485 GHz[4]) from fixed and mobile devices, and building personal area networks (PANs). [Wikipedia](https://en.wikipedia.org/wiki/Bluetooth)

### Bluetooth Low Energy

> Bluetooth low energy (Bluetooth LE, BLE, marketed as Bluetooth Smart[1]) is a wireless personal area network technology designed and marketed by the Bluetooth Special Interest Group aimed at novel applications in the healthcare, fitness, beacons,[2] security, and home entertainment industries.[3] Compared to Classic Bluetooth, Bluetooth Smart is intended to provide considerably reduced power consumption and cost while maintaining a similar communication range ... *From Wikipedia, the free encyclopedia*

- [Wikipedia Bluetooth Profiles](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles)
- [Gateway Smart Starter Kit](https://www.bluetooth.com/develop-with-bluetooth/developer-resources-tools/gateway?s=google2016&gclid=Cj0KEQiA3t-2BRCKivi-suDY24gBEiQAX1wiXFnagz0rAOa1bUa8ySwFFisOAraUewlTnmDWuG77-X0aAo128P8HAQ)

### BlueTooth Smart Mesh

- [EETimes BlueTooth Smart Mesh](http://www.eetimes.com/document.asp?doc_id=1325815)

### iBeacon

> iBeacon is a protocol developed by Apple and introduced at the Apple Worldwide Developers Conference in 2013. Various vendors have since made iBeacon-compatible hardware transmitters - typically called beacons - a class of Bluetooth low energy (LE) devices that broadcast their identifier to nearby portable electronic devices. The technology enables smartphones, tablets and other devices to perform actions when in close proximity to an iBeacon. [Wikipedia](https://en.wikipedia.org/wiki/IBeacon)

- [Estimote](http://estimote.com/)

### BlueTooth @ Intel® Edison

- [Intel® Edison Bluetooth Guide](http://www.intel.com/support/edison/sb/CS-035381.htm)
- [Intel® Edison SPP](https://software.intel.com/en-us/articles/connecting-the-intel-edison-board-to-your-android-phone-with-serial-port-profile-spp)

#### Pairing

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

#### BlueTooth Headsets

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

## LoRa

> LoRa® Alliance is an open, non-profit association of members that believe the internet of things era is now. Our mission to standardize Low Power Wide Area Networks (LPWAN) being deployed around the world to enable Internet of Things (IoT), machine-to-machine (M2M), and smart city, and industrial applications. The Alliance members will collaborate to drive the global success of the LoRa protocol (LoRaWAN), by sharing knowledge and experience to guarantee interoperability between operators in one open global standard.

> LoRaWAN is designed to provide Low Power Wide Area Network with features specifically needed to support low-cost, mobile, secure bi-directional communication for Internet of Things (IoT), machine-to-machine (M2M), and smart city, and industrial applications. It is optimized for low power consumption and to support large networks with millions and millions of devices. It has innovative features, support redundant operation, location, low-cost, low-power and can even run on energy harvesting technologies enabling the mobility and ease of use to Internet of Things.

- [LoRa Homepage](https://www.lora-alliance.org/)

## ZigBee

> ZigBee is a specification for a suite of high-level communication protocols used to create personal area networks built from small, low-power digital radios. ZigBee is based on an IEEE 802.15.4 standard. Its low power consumption limits transmission distances to 10–100 meters line-of-sight, depending on power output and environmental characteristics ... *From Wikipedia, the free encyclopedia*

[ZigBee Alliance](http://www.zigbee.org/)

## Z-Wave

> Z-Wave is a wireless communications specification designed to allow devices in the home (lighting, access controls, entertainment systems and household appliances, for example) to communicate with one another for the purposes of home automation ... *From Wikipedia, the free encyclopedia*

- [Z-Wave Homepage](http://www.z-wave.com/)
- [Post Z-Wave Data to Node Red](https://www.ibm.com/developerworks/community/blogs/cee6c09c-a315-4b04-ad14-57d6a60fa8bb/entry/post_z_wave_data_to_node_red?lang=en)

## Thread

> One of the younger standards in the IoT world used by the Google-owned smart home appliances startup Nest. The working group behind the standard includes Samsung, ARM Holdings, Freescale, Silicon Labs, and Big Ass Fans. Thread creates an IP-addressable mesh network with up to 250 devices that supports cloud access and AES encryption.

[Thread Group Homepage](http://threadgroup.org/)

## HomeKit

> HomeKit is supposed to be a platform that unites Apple-made and Apple-certified devices via Wi-Fi and Bluetooth. Apple has already revealed a list of partners that includes iHome, Haier, Withings, Philips, iDevices, Belkin, Honeywell, and Kwikset.

