#include <Servo.h>


//# MT_ECE_Who-_Rumplestiltskin
//Final Project for Media and Technology Spring 23, Interactive Fairytale

//READ ME
/*
Our project follows the fairytale Rumpelstiltskin. A girl is forced to turn straw into gold and she gets the help of an unamed creature. However, she must give payment for his help, so she offers him money, jewels, and her first child. Time passes and she gives birth to her first child. The creature returns and requests his promised payment, but gives her the chance to keep her child if she can guess his name. In the original story, she is able to guess it. However, in our enclosure we gave the user the ability to chose the fate of the baby.

In our project, we want to easily tell the story of Rumpelstiltskin while giving the user a choice to pick an ending. We wanted to guide the user through the story with simple interactions, taking the user through 3 scenes. At the end, the user will decide the ending by picking the right or wrong name.
*/


//PSEUDO CODE
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





