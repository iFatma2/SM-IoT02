# SM-IoT02

## ![SM23-IoT02](https://github.com/iFatma2/SM-IoT02/assets/139279448/26ae292f-a89b-4260-a868-7edc60f3005e)

## Introduction
  - The main objective of the second task of the Internet of Things path is to connect two Arduino pieces to work together. When the pushbutton is clicked on the first Arduino, the LED on the second Arduino is turned on.

  - The task was simulated in Tinkercad.



## The components

   - Arduino (2)

   - LED (1)

   - Wires to connect

   - Pushbutton (1)

   - Resistors (2)







## Testing 

  - Video test

  

   https://github.com/iFatma2/SM-IoT02/assets/139279448/8fd2c258-d9d9-4658-8d7e-fdddbfc63efc






## The code 

### Frist Arduino with Pushbutton.
```
#include <Wire.h>

int pushButton = A0;
int x = 0;

void setup()
{
  Wire.begin();
  pinMode(pushButton, INPUT);
}

void loop()
{
   Wire.beginTransmission(1);
   x = digitalRead(pushButton);
   Wire.write(x);
   Wire.endTransmission();
   delay(500);
}
```


### Second Arduino with Red LED.
```
#include <Wire.h>

int pinLed=13;
int x =0;

void setup()
{
  Wire.begin(1);
  Wire.onReceive(receiveEvent); 
  pinMode(pinLed, OUTPUT);
}

void loop()
{
  delay(100);
}

void receiveEvent(int howMany){

x = Wire.read();
  
  if (x == 1){
  
        digitalWrite(pinLed,HIGH);
  }
  else{
        digitalWrite(pinLed,LOW);
  }
}
```
