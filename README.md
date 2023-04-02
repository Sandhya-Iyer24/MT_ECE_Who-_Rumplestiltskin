//# MT_ECE_Who-_Rumplestiltskin
//Final Project for Media and Technology Spring 23, Interactive Fairytale






















//button code
const int buttonPin = 2;
int buttonState = 0;
int previousButtonState = 0;

void setup() {
  pinMode(buttonPin, INPUT);
  Serial.begin(9600);
}

void loop() { // turn this into function with parameters
  buttonState = digitalRead(buttonPin);

  if(buttonState != previousButtonState) {
    if(buttonState == HIGH) {
      return true;
    } else {
      return false;
    }
  }
  previousButtonState = buttonState;
}
