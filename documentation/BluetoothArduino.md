# Arduino

HC-06

```c
#include <SoftwareSerial.h>
 
SoftwareSerial mySerial(6, 5);
int dataFromBT;
 
void setup() {
  Serial.begin(57600);
  Serial.println("Service Available!");
  mySerial.begin(115200);
  pinMode(13, OUTPUT);   
}
 
void loop() {
  if (mySerial.available())
    dataFromBT = mySerial.read();
 
  if (dataFromBT == '0') {
    digitalWrite(13, LOW);
  } else if (dataFromBT == '1') {
    digitalWrite(13, HIGH);
  }
}
```