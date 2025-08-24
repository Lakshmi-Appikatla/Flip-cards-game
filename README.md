# Flip-cards-game
A game which is developed by using python code.............
import random

# Create board (pairs of letters)
cards = list("AABBCCDD")
random.shuffle(cards)

# Hide cards with *
board = ["*"] * len(cards)

def display_board():
    print(" ".join(board))

def play_game():
    attempts = 0
    matched = 0

    while matched < len(cards):
        display_board()
        try:
            # Pick first card
            i = int(input("Pick first card (0-7): "))
            if board[i] != "*":
                print("Already revealed! Try again.")
                continue

            board[i] = cards[i]
            display_board()

            # Pick second card
            j = int(input("Pick second card (0-7): "))
            if board[j] != "*":
                print("Already revealed! Try again.")
                board[i] = "*"  # reset first choice
                continue

            board[j] = cards[j]
            display_board()

            attempts += 1

            # Check match
            if cards[i] == cards[j]:
                print("✅ Match found!")
                matched += 2
            else:
                print("❌ Not a match!")
                board[i] = "*"
                board[j] = "*"

        except (ValueError, IndexError):
            print("Invalid input, try again.")

    print(f"🎉 You won in {attempts} attempts!")
