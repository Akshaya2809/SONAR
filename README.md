# SONAR
This repo has  the codes of my academic project sonar.
Author - Akshaya Sekar
<br>

#include<Servo.h>

#define trigPin 8
#define echoPin 9
#define ledPin 13
#define buzPin 7

long duration;
int distance ;
 int i ;
Servo myservo;

int calculateDistance()
{
  digitalWrite(trigPin,LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin,HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin,LOW);
  duration = pulseIn(echoPin, HIGH);
  distance = duration*0.034/2;
  return distance;
}

void setup()
{
  pinMode(trigPin , OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(ledPin , OUTPUT);
  pinMode(buzPin , OUTPUT);
  myservo.attach(11);
  myservo.write(0);
  Serial.begin(9600);
}

void loop()
{

 for (i=0; i<=150; i++)
 {
  myservo.write(i);
  delay(5);
  calculateDistance();
  Serial.print(i);
  Serial.print(",");
  Serial.print(distance);
  Serial.print(".");
 }
 for(i=150; i>=0; i--)
 {
  myservo.write(i);
  delay(5);
  calculateDistance();
  Serial.print(i);
  Serial.print(",");
  Serial.print(distance);
  Serial.print(".");
  
 }
 <br>
 

}
