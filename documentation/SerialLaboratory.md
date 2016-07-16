# Laboratory

## Intel Edison

```sh
root@edison:~# stty -F /dev/ttyMFD1 9600
```

```python

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