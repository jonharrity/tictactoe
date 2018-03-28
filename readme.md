# Tic-Tac-Toe


### Abstract

This project is a terminal-based tic-tac-toe game between a user and an AI. The Program uses the minimax algorithm with alpha/beta pruning. 


### Introduction

The problem is the find an effective method to calculate the best move to make in a tic-tac-toe game. Using optimal solutions only by each player, it is possible to tie every single game; therefore, an optimal program will never lose. The minimax algorithm is chosen for the task due to the ability to look ahead several moves, find the best move for the computer and mitigate the best moves the human player can make. Alpha/beta pruning, while a small part of the algorithm, makes a big improvement to the calculation speed by eliminating unnecesary calculations. 


### Problem Definition

Tic-tac-toe is a turn-based game between two players on a 3x3 grid. Each turn the player places either an 'x' or an 'o' based upon their assigned identifier, which stays constant throughout the game. A player wins by having three of their identifiers in a row, column, or diagonal. Oftentimes, the game board will fill up without either player winning.


### Methods

The minimax algorithm starts from the perspective of the computer, and selects the best move based upon minimizing what the best move of the opponent will be, which is selected by minimizing the best move of the AI, and so on recursively until a terminal state is reached. An effective evaluation function is necessary to assign a value (positive for the AI, negative for the player) for the min and max functions to accomplish this task. Alpha/beta pruning is a tactic for optimizing this algorithm by setting clever limitations on which nodes the program will evaluate; if the program recognized that nodes are not worth exploring, the nodes will be 'pruned' or discarded.
The evaluation function used in this program, relative to a specific square on the game board, returns a value positive or negative based on whether filling the square is beneficial to the AI or to the user. This value becomes closer to zero for each turn it will take to reach this terminal game state. For example, if the AI can select a square at (0,0) to win the game in three moves, the score of that node becomes (15-3)=12. This prioritizes moves that will win in fewer turns. The evaluation function also adds points for blocking the opponents win in the same way.


### Results

The AI never loses a game, as desired. There is no noticable lag for the AI computations (they are apparently instant). Output of 10 games can be seen in "output.txt", where the AI wins 4 times, and ties 6 times. In addition the the algorithm, supporting code provides a pretty-printed terminal interface for playing the game. Pressing control-c in the terminal will exit the program before the game is over.


### Conclusions and Discussions

Initially the evaluation function was based off how many squares in the same row/column/diagonal were filled, but this did not effectively prioritize blocking the opponent, and when adding positive and negative values for both the user and AI squares, the score would cancel out, providing skewed scores. The current evaluation function solves this problem. 
I copied the output by using the "tee" proram to write stdout to a temporary text file (python3 tictactoe.py | tee tmp) and appending the output to "output.txt" so that I could record the stdout of the program while still seeing the output in the terminal to be able to play the game. As a result, stdin was not recorded so user input lines appear as "Enter x value: Enter y value:" but one can still see where the user moved by looking at the subsequently printed game board. 
Before alpha/beta pruning, the AI would take a good second at the first move (later moves were much faster), but with alpha/beta pruning, there is no noticable lag even for the first move.


### References

The only resources used to complete this assignment are the minimax and alpha/beta algorithm description provided by powerpoint during class, and the man page for the unix "tee" program.


#### Written by Jon Harrity (3/14/18)
 
