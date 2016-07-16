# Laboratory

## Intel Edison

```sh
root@edison:~# stty -F /dev/ttyMFD1 9600
```

```python
from time import sleep
import serial
import mraa

x=mraa.Uart(0)

ser = serial.Serial('/dev/ttyMFD1', 9600) # Establish the connection on a specific port

counter = 32 # Below 32 everything in ASCII is gibberish

while True:
     counter +=1
     ser.write(str(chr(counter))) # Convert the decimal number to ASCII then send it to the Arduino
     print ser.readline() # Read the newest output from the Arduino
     sleep(.1) # Delay for one tenth of a second
     if counter == 255:
         counter = 32
```

## Arduino IDE

```c
#include <SoftwareSerial.h>

SoftwareSerial mySerial(0, 1); // RX, TX

void setup()
{
  Serial.begin(115200);
  mySerial.begin(9600);
  mySerial.println("Hello, world?");
}

void loop()
{
  mySerial.println("Hello World Serial");
  if (mySerial.available())
    Serial.write(mySerial.read());
}
```