// defining pins for ultrasonic sensor
const int trigPin = 9;
const int echoPin = 10;
const int led = 13;
const int buzzer = 11;
//defining variables duration and distance
long duration;
int distance;

void setup() {
  // put your setup code here, to run once:
// intializing baud rate
Serial.begin(9600);
pinMode(trigPin, OUTPUT);
pinMode(led,OUTPUT);
pinMode(echoPin,INPUT);
pinMode(buzzer,OUTPUT);
}

void loop() {
  // put your main code here, to run repeatedly:
  digitalWrite(trigPin,LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin,HIGH);
  delay(10);
  digitalWrite(trigPin,LOW);
  duration= pulseIn(echoPin,HIGH); 
  distance = duration*(0.034 / 2.0);

  if (distance<=15)  { digitalWrite(led,HIGH);
  tone(buzzer,100);
delay(500);
noTone(buzzer);
delay(500);}
  else { digitalWrite(led,LOW);
  noTone(buzzer);}

  Serial.print("Distance");
  Serial.println(distance);
}
