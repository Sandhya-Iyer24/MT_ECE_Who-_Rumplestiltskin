#include <Servo.h>


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
const int s1PullTab = 3;
const int s2GirlPlace = 5;
const int s3GirlPlace = 7;
const int s2Payment = 9;
const int s3Jack = 4;
const int s3Harry = 8;
const int s3Rumple = 5;

//servo variable
Servo s1strawGold;
const int servo1 = 2;
Servo s3baby;
const int servo2 = 6;

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
  //BUTTONS
  pinMode(s1PullTab, INPUT);
  pinMode(s2GirlPlace, INPUT);
  //pinMode(s2Payment, INPUT);
  pinMode(s3Jack, INPUT);
  pinMode(s3Harry, INPUT);
  pinMode(s3Rumple, INPUT);

  //SERVOS
  s1strawGold.attach(2);
  s1strawGold.write(0);
  pinMode(servo1, INPUT);
  s3baby.attach(6);
  s3baby.write(90);
  pinMode(servo2, INPUT);

  //LEDs
  pinMode(nextLED1, OUTPUT);
  pinMode(nextLED2, OUTPUT);
  pinMode(sadEndLED, OUTPUT);
  pinMode(happyEndLED, OUTPUT);
}

void loop() {
//SCENE 1
  if (digitalRead(s1PullTab) == HIGH) {
    s1strawGold.write(180);
    Serial.println("moved");
    digitalWrite(nextLED1, HIGH);
    scene1Done = true;
  }
    
//SCENE 2
   if((scene1Done == true) && (digitalRead(s2GirlPlace) == HIGH)) {
       digitalWrite(nextLED1, LOW);
     if (digitalRead(s2Payment) == HIGH)) {
  //     digitalWrite(nextLED2, HIGH);
  //     scene2Done = true;
  //   }
   }

 //SCENE 3         
  // if(digitalRead(s3GirlPlace) == HIGH) {
  //   //(scene1Done == true) && (scene2Done == true) &&
  //   digitalWrite(nextLED2, LOW);
  //   if((digitalRead(s3Jack) == HIGH) || (digitalRead(s3Harry) == HIGH)) {
  //     s3baby.write(0);
  //     digitalWrite(sadEndLED, HIGH);
  //     scene3Done = true;
      
  //   } else if (digitalRead(s3Rumple) == HIGH){
  //     s3baby.write(180);
  //     digitalWrite(happyEndLED, HIGH);
  //     scene3Done = true;
  //   }
  // }

}



