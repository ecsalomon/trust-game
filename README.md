# Trust Game with Punishment
This is a Javascript implementation of a modified multi-round trust game with a simulated second player, developed for my dissertation. 

A [working demo of the game](http://www.erikasalomon.com/trust) with 4 rounds is available.

## Classic Trust Game
The [classic trust game](https://en.wikibooks.org/wiki/Bestiary_of_Behavioral_Economics/Trust_Game) is an economic game for two players, where the outcome relies on trust between the players. The first player is given an amount of money and must decide how much money to entrust to the second player. This amount is passed to the second player by the experimenter, who triples it before giving it to the second player. The second player then decides how much money to return to player 1, and the game concludes. An example game may proceed as follows:

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
+ Players complete multiple rounds, each round being matched against a "different" simulated Player 2
+ On half (randomly assigned) of the rounds, Player 1 is allowed to punish player 2 if they think Player 2 played unfairly.

The second player is programmed to follow one of two rules (randomly assigned at the beginning of the game):

1. Player 2 is always generous, returning 40% to 60% of the tickets received to player 1 (exact amount randomly determined each round)
2. Player 2 behaves differently depending on whether the first player has the power to punish the Player 2:
  + **When player 1 *CANNOT* punish:** Player 2 behaves generously, as under the first rule 
  + **When player 1 *CAN* punish:** Player 2 behaves selfishly, returning 0% to 20% of the tickets they receive (exact amount randomly determined each round)

## Using the Game
This game was written to work within Qualtrics survey software; however, if you are comfortable with web development, you may use the index.html and game-style.css pages to create your own implementation. 

If you are using Qualtrics, the simplest way to implement this trust game is to import the Trust_Game_Template.qsf file into Qualtrics. This will default to a 24 round game with 12 "controller" (punishment option) rounds. If you wish to change the number of rounds, you will need to update the javascript in the game "question." To do this, click on the organge "JS" button next to the question titled "game" and edit the section of the code that looks like this:

![Game settings](/gamesettings.png) 

If you change number of rounds, you will also need to update the embedded variables in the survey flow. For each round *X*, your survey flow will need to have the variables *controllerX* (whether Player 1 was controller that round), *gaveX* (how many tickets Player 1 gave that round), *returnedX* (how many tickets Player 2 returned that round), and *punishX* (whether Player 1 punished Player 2 that round) to store the results of the game. The survey template defaults to 24 rounds with the appropriate variables in the survey flow. If you change the number of rounds, you will need to add or subtract the appropriate number of variables from your survey flow.

Once you have the template imported, you will need to upload the graphics used in the game to your Qualtrics account and update the links in the javascript to use those files. 
