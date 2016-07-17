# Linux and Arduino

Credits to [Github Daniela Plascencia DnPlas](https://github.com/dnplas)

## Arduino Based Development Board

```c
/*
   Copyright (c) 2015 Intel Corporation.  All rights reserved.

   This library is free software; you can redistribute it and/or
   modify it under the terms of the GNU Lesser General Public
   License as published by the Free Software Foundation; either
   version 2.1 of the License, or (at your option) any later version.

   This library is distributed in the hope that it will be useful,
   but WITHOUT ANY WARRANTY; without even the implied warranty of
   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
   Lesser General Public License for more details.

   You should have received a copy of the GNU Lesser General Public
   License along with this library; if not, write to the Free Software
   Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301  USA
*/
#include <CurieBLE.h>

BLEPeripheral blePeripheral;  // BLE Peripheral Device (the board you're programming)
BLEService ledService("19B10000-E8F2-537E-4F6C-D104768A1214"); // BLE LED Service

// BLE LED Switch Characteristic - custom 128-bit UUID, read and writable by central
BLEUnsignedCharCharacteristic switchCharacteristic("19B10001-E8F2-537E-4F6C-D104768A1214", BLERead | BLEWrite);

const int ledPin = 13; // pin to use for the LED

void setup() {
  Serial.begin(9600);

  // set LED pin to output mode
  pinMode(ledPin, OUTPUT);

  // set advertised local name and service UUID:
  blePeripheral.setLocalName("LED");
  blePeripheral.setAdvertisedServiceUuid(ledService.uuid());

  // add service and characteristic:
  blePeripheral.addAttribute(ledService);
  blePeripheral.addAttribute(switchCharacteristic);

  // set the initial value for the characeristic:
  switchCharacteristic.setValue(0);

  // begin advertising BLE service:
  blePeripheral.begin();

  Serial.println("BLE LED Peripheral");
}

void loop() {
  // listen for BLE peripherals to connect:
  BLECentral central = blePeripheral.central();

  // if a central is connected to peripheral:
  if (central) {
    Serial.print("Connected to central: ");
    // print the central's MAC address:
    Serial.println(central.address());

    // while the central is still connected to peripheral:
    while (central.connected()) {
      // if the remote device wrote to the characteristic,
      // use the value to control the LED:
      if (switchCharacteristic.written()) {
        if (switchCharacteristic.value()) {   // any value other than 0
          Serial.println("LED on");
          digitalWrite(ledPin, HIGH);         // will turn the LED on
        } else {                              // a 0 value
          Serial.println(F("LED off"));
          digitalWrite(ledPin, LOW);          // will turn the LED off
        }
      }
    }

    // when the central disconnects, print it out:
    Serial.print(F("Disconnected from central: "));
    Serial.println(central.address());
  }
}
```

## Linux Based Development Board

```sh
root@edison:~# rfkill unblock bluetooth
root@edison:~# bluetoothctl
[NEW] Controller 98:4F:EE:04:1A:8C MyEdison [default]
[NEW] Device 98:4F:EE:0F:2B:E0 ARDUINO 101-2BE0
[NEW] Primary Service
        /org/bluez/hci0/dev_98_4F_EE_0F_2B_E0/service0009
        Vendor specific
[NEW] Characteristic
        /org/bluez/hci0/dev_98_4F_EE_0F_2B_E0/service0009/char000a
        Vendor specific
[NEW] Device 98:4F:EE:06:1B:99 edison
[NEW] Device 2C:D0:5A:80:7A:44 AARCEMOR-MOBL3
[NEW] Device 40:78:6A:26:4A:C2 XT1008
[bluetooth]# 
```

```sh
[bluetooth]# scan on
Discovery started
[CHG] Controller 98:4F:EE:04:1A:8C Discovering: yes
[NEW] Device 98:0D:2E:CD:84:90 Victoretorotavi
[NEW] Device 60:D8:19:AF:8F:12 CDAVALOX-MOBL
[NEW] Device C8:FF:28:A0:71:1C LAPASXA10W10
[NEW] Device E8:B1:FC:09:6A:FE ubuntu-gnome-0
[NEW] Device 98:4F:EE:06:44:E5 98-4F-EE-06-44-E5
[CHG] Device 98:4F:EE:06:44:E5 RSSI: -64
[CHG] Device 98:4F:EE:06:44:E5 TxPower: 0
[CHG] Device 98:4F:EE:06:44:E5 Name: edison
[CHG] Device 98:4F:EE:06:44:E5 Alias: edison
[CHG] Device 98:4F:EE:06:44:E5 Modalias: usb:v1D6Bp0246d0525
[CHG] Device 98:4F:EE:06:44:E5 UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Device 98:4F:EE:06:44:E5 UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Device 98:4F:EE:06:44:E5 UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Device 98:4F:EE:06:44:E5 UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Device 98:4F:EE:06:44:E5 UUIDs: 0000111e-0000-1000-8000-00805f9b34fb
[CHG] Device 98:4F:EE:06:44:E5 UUIDs: 0000110a-0000-1000-8000-00805f9b34fb
[CHG] Device 98:4F:EE:06:44:E5 UUIDs: 0000110b-0000-1000-8000-00805f9b34fb
[CHG] Device 98:0D:2E:CD:84:90 RSSI: -71
[CHG] Device 98:0D:2E:CD:84:90 RSSI: -71
[CHG] Device 98:4F:EE:0F:2B:E0 Connected: no
[CHG] Device 98:4F:EE:0F:2B:E0 RSSI: -61
[CHG] Device 98:4F:EE:0F:2B:E0 Name: LED
[CHG] Device 98:4F:EE:0F:2B:E0 Alias: LED
[bluetooth]# scan off       
[CHG] Device 98:4F:EE:0F:2B:E0 RSSI is nil
[CHG] Device 98:4F:EE:06:44:E5 TxPower is nil
[CHG] Device 98:4F:EE:06:44:E5 RSSI is nil
[CHG] Device E8:B1:FC:09:6A:FE TxPower is nil
[CHG] Device E8:B1:FC:09:6A:FE RSSI is nil
[CHG] Device C8:FF:28:A0:71:1C TxPower is nil
[CHG] Device C8:FF:28:A0:71:1C RSSI is nil
[CHG] Device 60:D8:19:AF:8F:12 TxPower is nil
[CHG] Device 60:D8:19:AF:8F:12 RSSI is nil
[CHG] Device 98:0D:2E:CD:84:90 TxPower is nil
[CHG] Device 98:0D:2E:CD:84:90 RSSI is nil
Discovery stopped
[CHG] Controller 98:4F:EE:04:1A:8C Discovering: no
[bluetooth]# 
```

```sh
[bluetooth]# connect 98:4F:EE:0F:2B:E0
Attempting to connect to 98:4F:EE:0F:2B:E0
[CHG] Device 98:4F:EE:0F:2B:E0 Connected: yes
Connection successful
[LED]# 
```

```sh
[LED]# list-attributes 
Primary Service
        /org/bluez/hci0/dev_98_4F_EE_0F_2B_E0/service0009
        Vendor specific
Characteristic
        /org/bluez/hci0/dev_98_4F_EE_0F_2B_E0/service0009/char000a
        Vendor specific
[LED]# 
```

```sh
[LED]# select-attribute /org/bluez/hci0/dev_98_4F_EE_0F_2B_E0/service0009/char000a
```

```sh
[LED:/service0009/char000a]# read 
Attempting to read /org/bluez/hci0/dev_98_4F_EE_0F_2B_E0/service0009/char000a
[CHG] Attribute /org/bluez/hci0/dev_98_4F_EE_0F_2B_E0/service0009/char000a Value: 0x00
  00                                               .               
[LED:/service0009/char000a]# write 01
Attempting to write /org/bluez/hci0/dev_98_4F_EE_0F_2B_E0/service0009/char000a
[LED:/service0009/char000a]# write 00
Attempting to write /org/bluez/hci0/dev_98_4F_EE_0F_2B_E0/service0009/char000a
[LED:/service0009/char000a]# 
```