The final project for a class on OOP. It is capable of playing 3 games: [Reversi](https://en.wikipedia.org/wiki/Reversi), [Nine Almonds](http://www.pedagonet.com/mathgenius/test229.html), and [Magic Square](https://en.wikipedia.org/wiki/Magic_square). To play each:

Lab4_final.exe Reversi <Player1_Name> <Player2_Name> <br/>
Lab4_final.exe MagicSquare [integer board dimension] [minimum integer piece value] <br/>
Lab4_final.exe NineAlmonds


Main file: Lab4_final.cpp


We implemented a smart pointer that can point to an instance of any one of the games, and construct that instance in dynamic memory. This meant we never had to deal with memory leaks.

In terms of saving the game, we added a save file method to the GameBase class in order to have it implemented across all of the games. If the user chooses to save, the save file reads in the name of the game and saves it to the first line. The board size is also saved. The gameboard is then printed line by line with each gamepiece on the line. This way when we use getline to load a game file we can use the line as its position on the gameboard. For example, line 29 in the save file would represent the 30th position in the game board. 2 dimensional coordinates are mapped to 1 dimensional coordinates using the formula x*width+y. If the user chooses to not save the file then NO DATA will be entered on the first line.

The GameBase constructor handles loading the data and reads in everything passed into it with getline. We use a bool to track if the file is successfully loaded. If loading is successful, we construct each individual game with the read-in file. If the load file bool is false then we construct the starting position of the game. 

The user can quit and save at any point. If the user decides to use different names in the next Reversi game then those changed names will be reflected. If no file exists then that file will be made if the user chooses to save. 

Copy Control Features:

We implemented a singleton design pattern so there is only one instance of the game at the time. There is no
need for copy, move constructors or assignment operators. A player cannot switch games, he/she can only end
and restart a new game. The only constructor implemented is the default constructor that can inherit
from the abstract base class. The shared smart pointer lets us handle destruction effectively as well. 