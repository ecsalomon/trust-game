# trust-game
This is a Javascript implementation of simulated modified multi-round trust game, developed for my dissertation.

## Classic Trust Game
In the classic trust game, the first player is given an amount of money and must decide how much money to entrust to the second player. The money given to the second player is tripled by the experimenter. The second player then decides how much money to return to player 1, and the game concludes. And example game my be run as follows:

+ Player 1 receives $10
+ Player 1 gives $8 to player 2
+ The experimenter triples the value of the donated money
+ Player 2 receives $24 ($8 * 3)
+ Player 2 keeps $15 and returns $9
+ Player 1 ends the game with $11 ($9 + ($10 - $8)), and Player 2 ends with $15
 
## Modifications
The game contains several modifications to the classic trust game:

+ Player 2 is simulated by the computer
+ Instead of money, participants are playing with raffle tickets
+ Players complete multiple rounds, each round being matched against a "different" simulated player 2
+ On half (randomly assigned) of the rounds, Player 1 is allowed to punish Player 2 if they think Player 2 played unfairly.

The second player is programmed to follow one of two rules (randomly assigned at the beginning of the game). Under one rule, player 2 is always generous, returning 40% to 60% of the tickets received to player 1 (amount randomly determined each round). Under the second rule, player 2 behaves differently depending on whether the first player has the power to punish the second player. When the first player *cannot* punish, player 2 behaves generously, as under the first rule. However, when player 1 has the ability to punish player 2, player 2 behaves selfishly, returning 0% to 20% of the tickets they receive.

A working demo of the game with 4 rounds can be played at http://www.erikasalomon.com/trust

## Using the Game
This game was written to work within Qualtrics survey software; however, if you are comfortable with web development, you may use the index.html and game-style.css pages to create your own implementation. If you are using Qualtrics, the simplest way to implement the trust game is to import the Trust_Game_Template.qsf file into Qualtrics. This will default to a 24 round game with 12 "controller" (punishment option) rounds. If you wish to change the number of rounds, you will need to update the javascript in the game "question" and update the survey flow so that the correct variables are present.

Once you have the template imported, you will need to upload the graphics used in the game to your Qualtrics account and update the links in the javascript to use those files. 
