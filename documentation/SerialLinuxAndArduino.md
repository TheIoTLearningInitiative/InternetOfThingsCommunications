# Linux And Arduino

## Linux Based Development Board

```sh
root@edison:~# stty -F /dev/ttyMFD1 9600
```

```sh
root@edison:~# nano helloserial.py
```

```python
from time import sleep
import serial
import mraa

x=mraa.Uart(0)

ser = serial.Serial('/dev/ttyMFD1', 9600)

while True:
     print ser.readline()
     sleep(.1)
```

```sh
root@edison:~# python helloserial.py
```

## Arduino Based Board

```c
#include <SoftwareSerial.h>

SoftwareSerial mySerial(0, 1);

void setup()
{
  mySerial.begin(9600);
}

void loop()
{
  mySerial.println("Hello Serial!");
  if (mySerial.available())
    Serial.write(mySerial.read());
}
```