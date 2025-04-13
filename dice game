import random
import time

def roll_dice():
    return random.randint(1, 6)

def print_dice_face(number):
    dice_faces = {
        1: (
            "┌───────┐",
            "│       │",
            "│   ●   │",
            "│       │",
            "└───────┘"
        ),
        2: (
            "┌───────┐",
            "│ ●     │",
            "│       │",
            "│     ● │",
            "└───────┘"
        ),
        3: (
            "┌───────┐",
            "│ ●     │",
            "│   ●   │",
            "│     ● │",
            "└───────┘"
        ),
        4: (
            "┌───────┐",
            "│ ●   ● │",
            "│       │",
            "│ ●   ● │",
            "└───────┘"
        ),
        5: (
            "┌───────┐",
            "│ ●   ● │",
            "│   ●   │",
            "│ ●   ● │",
            "└───────┘"
        ),
        6: (
            "┌───────┐",
            "│ ●   ● │",
            "│ ●   ● │",
            "│ ●   ● │",
            "└───────┘"
        )
    }
    for line in dice_faces[number]:
        print(line)

def main():
    print("🎲 Welcome to the Dice Game! 🎲\n")
    while True:
        user_input = input("Press Enter to roll the dice or type 'q' to quit: ").lower()
        if user_input == 'q':
            print("\nThanks for playing! Goodbye.\n")
            break
        print("\nRolling the dice...")
        time.sleep(1)
        dice_number = roll_dice()
        print(f"\nYou rolled a {dice_number}!\n")
        print_dice_face(dice_number)
        print()

if __name__ == "__main__":
    main()
