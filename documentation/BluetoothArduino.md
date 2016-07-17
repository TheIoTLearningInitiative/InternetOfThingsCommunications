# Arduino

```c
#include <SoftwareSerial.h>
 
SoftwareSerial mySerial(6, 5);
int dataFromBT;
 
void setup() {
  Serial.begin(57600);
  Serial.println("LEDOnOff Starting...");
 
  // The data rate for the SoftwareSerial port needs to 
  // match the data rate for your bluetooth board.
  mySerial.begin(115200);
  pinMode(13, OUTPUT);   
}
 
void loop() {
  if (mySerial.available())
    dataFromBT = mySerial.read();
 
  if (dataFromBT == '0') {
    // Turn off LED
    digitalWrite(13, LOW);
  } else if (dataFromBT == '1') {
    // Turn on LEFD
    digitalWrite(13, HIGH);
  }
}
```