# the-number-scrabble-game
Each player chooses a number from one to nine, and whoever collects three numbers for a total of 15 wins
def main():
    # set numbers and welcome message
    numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9]
    player1_numbers = []
    player2_numbers = []
    print("Welcome to the number scrabble game")
    print(numbers)
    print("Player 1 numbers:", player1_numbers)
    print("Player 2 numbers:", player2_numbers)

    # game playing
    while True:
        # player1
        move = input("Player 1, please enter a number from the list: ")
        while not move.isdigit() or int(move) not in numbers:
            move = input("Player 1, please enter a number from the list: ")

        move = int(move)
        numbers.remove(move)
        player1_numbers.append(move)
        print("Player 1 numbers:", player1_numbers)
        print("Player 2 numbers:", player2_numbers)
        print(numbers)

        # Check win conditions for player 1
        if check_conditions(player1_numbers):
            print("Player 1 is the winner!")
            break

        # Check for draw
        if not numbers:
            print("It's a draw!")
            break

        # player2
        move = input("Player 2, please enter a number from the list: ")
        while not move.isdigit() or int(move) not in numbers:
            move = input("Player 2, please enter a number from the list: ")

        move = int(move)
        numbers.remove(move)
        player2_numbers.append(move)
        print("Player 1 numbers:", player1_numbers)
        print("Player 2 numbers:", player2_numbers)
        print(numbers)

        # Check win conditions for player 2
        if check_conditions(player2_numbers):
            print("Player 2 is the winner!")
            break

        # Check for draw after player 2's move
        if not numbers:
            print("It's a draw!")
            break


def check_conditions(numbers):
    n = len(numbers)
    for i in range(n):
        for j in range(i + 1, n):
            for k in range(j + 1, n):
                if numbers[i] + numbers[j] + numbers[k] == 15:
                    return True
    return False


main()
