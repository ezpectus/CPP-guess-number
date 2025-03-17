# C-guess-number
C++ easy project with guess the number , find secret number within 7 attempts
# Number Guessing Game with Binary Search in C++

This C++ program implements a number guessing game where the computer selects a random number between 1 and 100, and the player tries to guess it. The program uses the binary search algorithm to efficiently narrow down the search range.

## What it does

The program:

1.  **Generates a Secret Number:** Randomly selects a number between 1 and 100.
2.  **Implements Binary Search:** Uses binary search to make guesses and narrow down the range.
3.  **Provides Feedback:** Tells the player if the guess is too high or too low.
4.  **Announces the Result:** When the player guesses correctly, the program displays the number of attempts taken.

## How to use

1.  **Save the Code:** Save the C++ code in a file (e.g., `guess_number.cpp`).
2.  **Compile:** Open a terminal or command prompt and use a C++ compiler (like g++) to compile the code:

    ```bash
    g++ guess_number.cpp -o guess_number
    ```

3.  **Run:** Execute the compiled program:

    ```bash
    ./guess_number
    ```

    Follow the prompts to play the game.

## Code Explanation

```c++
#include <iostream>
#include <cstdlib>
#include <ctime>

using namespace std;

int main() {
    srand(time(0));

    int secret = rand() % 100 + 1; // Generate a random number between 1 and 100
    int low = 1, high = 100, guess, attempts = 0;

    cout << "I've picked a number between 1 and 100. Try to guess it!\n";

    while (true) {
        guess = low + (high - low) / 2; // Binary search guess
        attempts++;

        cout << "Your guess: " << guess << endl;

        if (guess == secret) {
            cout << "Congratulations! You guessed the number " << secret << " in " << attempts << " attempts!\n";
            break;
        } else if (guess > secret) {
            cout << "The secret number is lower.\n";
            high = guess - 1;
        } else {
            cout << "The secret number is higher.\n";
            low = guess + 1;
        }
    }

    return 0;
}
