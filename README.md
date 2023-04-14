const int trigPin = 9;
const int echoPin = 10;
const int ledPin = 6;
const int sensorPin = A0;
const int buttonPin = 2;
int distance;
int preferred = 0;
const int piezoPin = 8;
long duration;
int buttonState = 0;
int previousButtonState = 0;
#include "pitches.h"
int melody[] = {
  NOTE_G4
};
int noteDurations[] = {
  10
};



void setup() {
  pinMode(trigPin, OUTPUT);  // Sets the trigPin as an Output
  pinMode(ledPin, OUTPUT);
  pinMode(echoPin, INPUT);  // Sets the echoPin as an Input
  pinMode(buttonPin, INPUT);
  pinMode(piezoPin, OUTPUT);
  Serial.begin(9600);  // Starts the serial communication
}

void loop() {
  // read the state of the pushbutton value:
  buttonState = digitalRead(buttonPin);

  // ultrasonic sensor code:
  // Clears the trigPin
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  // Sets the trigPin on HIGH state for 10 micro seconds
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  // Reads the echoPin, returns the sound wave travel time in microseconds
  duration = pulseIn(echoPin, HIGH);
  // Calculating the distance
  distance = duration * 0.034 / 2;
  // Prints the distance on the Serial Monitor

    Serial.print("Distance: ");
    Serial.println(distance);


  if (buttonState != previousButtonState) {
    if (buttonState == HIGH) {
      Serial.println("button pressed");
      preferred = distance;
      Serial.println("PREFERRED:");
      Serial.println(preferred);
    } else {
      Serial.println("button released");
    }
  }

  previousButtonState = buttonState;
  for (int thisNote = 0; thisNote < 2; thisNote++) {
    if (distance == preferred) {
      digitalWrite(ledPin, HIGH);
      int noteDuration = 1000 / noteDurations[thisNote];
      tone(8, melody[thisNote], noteDuration);
      int pauseBetweenNotes = noteDuration * 1.30;
      delay(pauseBetweenNotes);

    } else {
      digitalWrite(ledPin, LOW);
      noTone(8);
    }
  }
}
