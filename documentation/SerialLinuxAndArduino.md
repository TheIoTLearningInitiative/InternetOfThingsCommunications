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
counter = 32

while True:
     counter +=1
     ser.write(str(chr(counter)))
     print ser.readline()
     sleep(.1)
     if counter == 255:
         counter = 32
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