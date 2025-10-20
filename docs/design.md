# The Main Design
## Problem Statement/target audience
The game save-the-watermelon is overall a word guessing game that allows the player to try and guess the randomly generated word correctly. The game is set up to be a new and accessiable way for beginner python coders to create a fun game but also to learn more about how python works. The main target audience are those who are up to play a word guessing game that comes with a fun challenge and beginner computer science students wanting to learn more about python.
## Game Rules and win/loose conditions
- When the player wants to play, the computer will generate a random secret word
- The secret word will be displayed as _ _ _ _ _ _
- The player will try and guess the secret word but can only use one letter at a time
- If the letter the player chooses is correct, the letter will reveal itself
- If the letter the player chooses is incorrect, the watermelon will loose one slice out of the six it holds
- If the player chooses all of the correct letters, the secret word will reveal itself and the player wins
- If the player looses all six slices before the secret word reveals itself, the player looses
- The player would have to get to zero slices to declared that they have lost
- After the game ends, the player will be asked y/n question on whether they would like to play again
## Core features vs Stretch goals
### Must have features
- The ability to replay
- Random secret word generator
- Having either win/loose messages at the end
- Guesses can only be made by single letters
### Stretch goals
- Different levels of difficulty
- A scoreboard of player vs computer
- Different categories
## Basic flow diagram or bullet flow
### Bullet
- Game start
- Secret word is picked
- Six slices
- Slices = -1
- The masked word appears
- Player puts down a letter
- Letter stays if correct
- Letter does not stay if incorrect
- Word is revealed when all correct letters are guessed
- A slice is docked when letter guess is incorrect
- End loop, see if win or loose
- Ask to play again
- Yes = play again
- No = do not play again
## Data Design
- str = secret word
- set[str] = the letters the player has already made a guess at
- int = number of slices left
- mask_word(secret, guessed) = the display form
## Module/Function Responsibilities
- words.py = load the word list
- words.txt = return the random word from the list
- logic.py
       - mask_word(secret, guessed)
       - validate_guess(raw, guessed)
       - apply_guess(secret, guessed, guess)
       - is_win(secret, guessed)
- game.py
- run the loop
- replay
- tests/test_logic.py = unit tests for the logic.py python file
