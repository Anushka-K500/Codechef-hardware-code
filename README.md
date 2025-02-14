# Codechef-hardware-code
// defining pins for ultrasonic sensor

const int trigPin = 19;
const int echoPin = 18;
const int led = 17;

//defining variables duration and distance

long duration;
int distance;

void setup() {

// put your setup code here, to run once:
// intializing baud rate

Serial.begin(115200)
pinMode(trigPin, OUTPUT);
pinMode(led, OUTPUT);
pinMode(echoPin, INPUT);

}

void loop() {

// put your main code here, to run repeatedly:

digitalWrite(trigPin, LOW);
delayMicroseconds(2);
digitalWrite(trigPin, HIGH);
delay(10);
digitalWrite(trigPin, LOW);

duration= pulseIn(echoPin, HIGH);
distance = duration* (0.034 / 2.0);

if (distance<=15) { digitalWrite(led, HIGH);}
else { digitalWrite(led, LOW); }

Serial.print("Distance");
Serial.println(distance);
}
