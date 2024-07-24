# Bluetooth-Servo-Motor
Bluetooth Servo Motor Controll
#include <Servo.h>

Servo myservo;  
int servoPin = 9;  
int currentAngle = 90; 

void setup() {
  Serial.begin(9600);  
  myservo.attach(servoPin);  
  myservo.write(currentAngle);  
}

void loop() {
  if (Serial.available() > 0) {  
    char command = Serial.read();  
  if (command == '1') {
      currentAngle += 90;
  if (currentAngle > 360) currentAngle = 360;
      myservo.write(currentAngle);
    } 
  else if (command == '2') {
      currentAngle -= 90;
  if (currentAngle < 0) currentAngle = 0;
      myservo.write(currentAngle);
    }
  }
}
