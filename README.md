# DC_motor_driver
- I am going to use channel B


pins per Ch. B
Direction		D13
PWM		D11
Brake		D8
Current Sensing		A1

Going to use PID library

//https://www.twovolt.com/2020/06/15/arduino-pid-brushed-dc-servo-motor-position-control-using-joystick/
#include <PID_v1.h>
#define M1 11 // PWM outputs to L298N H-Bridge motor driver module - pin 11
#define Brake 8 // Brake for the motor
#define Direction 13 // direction for motor


void setup() {

//TCCR1B = TCCR1B & 0b11111000 | 1; // set 31KHz PWM to prevent motor noise
//myPID.SetMode(AUTOMATIC);
//myPID.SetSampleTime(1);
//myPID.SetOutputLimits(-255, 255);  

  //Setup Channel B
  pinMode(13, OUTPUT); //Initiates Motor Channel B pin; Direction
  pinMode(8, OUTPUT); //Initiates Brake Channel B pin; Brake
  
Serial.begin (9600); // for debugging
}
loop(){
 //forward @ full speed
  digitalWrite(13, HIGH); //Establishes forward direction of Channel A
  digitalWrite(8, LOW);   //Disengage the Brake for Channel A
  analogWrite(11, 255);   //Spins the motor on Channel A at full speed
  
  delay(3000);
  
  digitalWrite(8, HIGH); //Eengage the Brake for Channel A

  delay(1000);
  
  //backward @ half speed
  digitalWrite(13, LOW); //Establishes backward direction of Channel A
  digitalWrite(8, LOW);   //Disengage the Brake for Channel A
  analogWrite(11, 123);   //Spins the motor on Channel A at half speed
  
  delay(3000);
  
  digitalWrite(8, HIGH); //Eengage the Brake for Channel A
  
  delay(1000);}
