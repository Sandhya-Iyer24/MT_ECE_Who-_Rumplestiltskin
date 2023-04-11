//# MT_ECE_Who-_Rumplestiltskin
//Final Project for Media and Technology Spring 23, Interactive Fairytale

/*If girl placed on marker 1
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
            “happily ever after” sign lights up (LED)*/


//copper tape "buttons"
const int s1GirlPlace = 2;
const int s1PullTab = 3;
const int s1StrawGold = 4;
const int s2GirlPlace = 5;
const int s2Payment = 6;
const int s3Jack = 7;
const int s3Harry = 8;
const int s3Rumple = 9;

//booleans
bool scene1Done = false;
bool scene2Done = false;
bool scene3Done = false;

//LEDs
const int nextLED1 = 10;
const int nextLED2 = 11;
const int sadEndLED = 12;
const int happyEndLED = 13;




void setup() {
  pinMode(s1GirlPlace, INPUT);
  pinMode(s1PullTab, INPUT);
  pinMode(s1StrawGold, INPUT);
  pinMode(s2GirlPlace, INPUT);
  pinMode(s2Payment, INPUT);
  pinMode(s3Jack, INPUT);
  pinMode(s3Harry, INPUT);
  pinMode(s3Rumple, INPUT);
}

void loop() {

  if (digitalRead(s1GirlPlace) == HIGH) {
    //Pull tab pops out (servos)
    if (digitalRead(s1PullTab) == HIGH) {
    //Straw turns to gold (servos)
      digitalWrite(nextLED1, HIGH);
      scene1Done = true;
    }
  }

  if((scene1Done == true) && (digitalRead(s2GirlPlace) == HIGH)) {
      digitalWrite(nextLED1, LOW);
    if (digitalRead(s2Payment) == HIGH)) {
      digitalWrite(nextLED2, HIGH);
      scene2Done = true;
    }
  }
          
  if((scene1Done == true) && (scene2Done == true) &&  (digitalRead(s3GirlPlace) == HIGH)) {
    digitalWrite(nextLED2, HIGH);
    if((digitalRead(s3Jack) == HIGH) || (digitalRead(s3Harry) == HIGH)) {
      //baby moves down (servos)
      digitalWrite(sadEndLED, HIGH);
    }
    else{
      //Rumplestiltskin turns into “poof” (servos)
      digitalWrite(sadEndLED, HIGH);
    }
  }

}



