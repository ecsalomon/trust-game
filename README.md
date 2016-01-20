# Trust Game with Punishment
This is a Javascript implementation of a modified multi-round trust game with a simulated second player, developed for my dissertation. 

A [working demo of the game](http://www.erikasalomon.com/trust) with 12 rounds is available.

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
+ On some of the rounds, Player 1 is allowed to punish Player 2 if they think Player 2 played unfairly.
+ On other rounds, Player 2 may punish Player 1 if they feel Player 1 gave too few tickets(punishment threshold is randomly set between 0 and 15 tickets on each round)

The second player is programmed to follow one of two rules (randomly assigned at the beginning of the game):

1. Player 2 always plays fairly, returning 45% to 55% of the tickets received to Player 1 (exact amount randomly determined each round)
2. Player 2 behaves differently depending on who has the ability to punish:
  + **When *Player 1* can punish:** Player 2 behaves stingily, returning 0% to 10% of the tickets they receive (exact amount randomly determined each round)
  + **When *Player 2* can punish:** Player 2 behaves generously, returning 60% to 70% of the tickets they receive (exact amount randomly determined each round)
  + **When *no one* has the ability to punish:** Player 2 behaved fairly, returning 45% to 55% of the tickets they receive(exact amount randomly determined each round)

The number of rounds played; the number of times each player has the ability to punish; the exact percentages of tickets returned by the fair, generous, and stingy Player 2; and whether the punishment assignments are blocked or randomized can be adjusted in the game settings.

## Using the Game
This game was written to work within Qualtrics survey software; however, if you are comfortable with web development, you may use the index.html and game-style.css pages to create your own implementation. 

If you are using Qualtrics, the simplest way to implement this trust game is to import the Trust_Game_Template.qsf file into Qualtrics. This will default to a 30 round game with 15 Player 1 punisher rounds and 15 player 2 punisher rounds. If you wish to change the number of rounds or any of the other variables, you will need to update the javascript in the game "question." To do this, click on the organge "JS" button next to the question titled "game" and edit the section of the code that looks like this:

![Game settings](/gamesettings.png) 

If you change number of rounds, you will also need to update the embedded variables in the survey flow. For each round *X*, your survey flow will need to have the variables *controllerX* (whether Player 1 was controller that round), *gaveX* (how many tickets Player 1 gave that round), *returnedX* (how many tickets Player 2 returned that round), and *punishX* (whether Player 1 punished Player 2 that round) to store the results of the game. The survey template defaults to 24 rounds with the appropriate variables in the survey flow. If you change the number of rounds, you will need to add or subtract the appropriate number of variables from your survey flow.

Once you have the template imported, you will need to upload the graphics used in the game to your Qualtrics account and update the links in the javascript to use those files. 
