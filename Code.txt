#include <SoftwareSerial.h> 

#include <Servo.h> 
Servo myservo; 
int bluetoothTx = 0; 
int bluetoothRx = 1; 
SoftwareSerial bluetooth(bluetoothTx, bluetoothRx);

void setup()
{
  myservo.attach(9); 

  Serial.begin(9600);

  
  bluetooth.begin(9600);
}

void loop()
{
  
  if(bluetooth.available()> 0 ) 
  {
    int servopos = bluetooth.read(); 
    Serial.println(servopos); 
    myservo.write(servopos); 

}
