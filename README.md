//# MT_ECE_Who-_Rumplestiltskin
//Final Project for Media and Technology Spring 23, Interactive Fairytale

If girl placed on marker 1
	Scene 1 begins
	Pull tab pops out (servos)
	If pull tab is pulled
		Straw turns to gold
		“Next Scene” LED lights up
    If girl placed on marker 2
      LED 1 turns off
      Scene 2 begins
      If “payment” meets other end
        LED 2 turns on
        If girl placed on marker 3
          LED 2 turns off
          Scene 3 begins
          If Jack or Harry button is pressed
            baby moves down (servos)
            “sad ending” lights up (LED)
          Else
            Rumplestiltskin turns into “poof” (servos)
            “happily ever after” sign lights up (LED)

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
