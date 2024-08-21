# Tic-Tac-Toe Game in Python

A simple command-line Tic-Tac-Toe game implemented in Python. This game allows two players to play against each other on the same computer.

## Table of Contents

- [Introduction](#introduction)
- [Usage](#usage)
- [How to Play](#how-to-play)
- [Game Algorithm](#game-algorithm)
- [License](#license)

## Introduction

Tic-Tac-Toe is a classic two-player game where players take turns marking a spot on a 3x3 grid. The first player to align three of their marks (either horizontally, vertically, or diagonally) wins the game. If all nine spots are filled without a winner, the game ends in a draw.

## Usage

### Requirements

- Python 3.x

### Installation

Clone this repository to your local machine:

```bash
git clone https://github.com/yourusername/tic-tac-toe.git
cd tic-tac-toe
python tic_tac_toe.py
```
## How To Play
- *How to Play*
	- *Game Start*: When the game starts, the board will be displayed as a 3x3 grid with numbers 1 through 9 representing each spot.
	- *Player Input*: The game alternates between two players, X and O. On their turn, each player is prompted to enter a number corresponding to the spot they wish to mark.
	- *Marking the Board*: After entering a valid number (1-9), the player's mark (X or O) will be placed on the chosen spot on the board.
	- *Win Condition*: The game checks after each move if a player has aligned three of their marks in a row, column, or diagonal.
	- *Draw Condition*: If all spots are filled without a winner, the game ends in a draw.
	- *Game End*: The game will display the final board and announce the winner or indicate that the game is a draw.

<img src="/src/USAGE.png" align="center" alt="Exapmle Photo" border="0">

## Game Algorithm
1. Initialize the Board: Create a list of 9 spaces representing the 3x3 grid.
```bash
board = [' ' for _ in range(9)]
```
2. - *Player Turn*: The game alternates between player X and player O.
	 - Prompt the player to choose a spot on the board (1-9).
	 - Subtract 1 from the input to match the list index.
```bash
move = int(input(f"Player {current_player}, choose your move (1-9): ")) - 1
```
3.  - *Input Validation*: Check if the selected spot is empty.
	 - If it is, place the current player's mark (X or O).
	 - If it is not, prompt the player to choose another spot.
```bash
if board[move] == ' ':
    board[move] = current_player
else:
    print("That spot is already taken. Try again.")
```
4. *Update Board*: Place the player's mark on the board.
```bash
board[move] = current_player
```
5. *Check for a Winner*: After each move, check if the current player has won by aligning three marks in a row, column, or diagonal.
```bash
def check_winner(board, player):
    win_conditions = [(0, 1, 2), (3, 4, 5), (6, 7, 8),
                      (0, 3, 6), (1, 4, 7), (2, 5, 8),
                      (0, 4, 8), (2, 4, 6)]
    for condition in win_conditions:
        if board[condition[0]] == board[condition[1]] == board[condition[2]] == player:
            return True
    return False
```
6. *Check for a Draw*: If all spots on the board are filled and no player has won, the game ends in a draw.
```bash
def is_draw(board):
    return all(spot != ' ' for spot in board)
```
7. *Switch Player*: After each turn, switch the current player.
```bash
current_player = 'O' if current_player == 'X' else 'X'
```
8. *Game Loop*: Repeat the process until a player wins or the game ends in a draw.
```bash
while True:
    print_board(board)
    # Player makes a move
    # Check for winner or draw
    # Switch player
```

## License

This project is licensed under the MIT License - see the LICENSE file for details.

### Additional Notes:
- The "How to Play" section provides step-by-step instructions for playing the game.
- The "Game Algorithm" section breaks down the logic used in the implementation, which can be useful for anyone looking to understand or modify the code.
