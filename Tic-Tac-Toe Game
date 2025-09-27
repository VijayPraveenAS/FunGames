# FunGames
#tictactoegameproject

import random

def display_board(board):
    print("+-------+-------+-------+")
    for row in board:
        print("|       |       |       |")
        print(f"|   {row[0]}   |   {row[1]}   |   {row[2]}   |")
        print("|       |       |       |")
        print("+-------+-------+-------+")


def enter_move(board):
    while True:
        try:
            move = int(input("Enter your move (1-9): "))
            if move < 1 or move > 9:
                print("Invalid number. Choose between 1 and 9.")
                continue
            for row in range(3):
                for col in range(3):
                    if board[row][col] == move:
                        board[row][col] = 'O'
                        return
            print("That square is already occupied.")
        except ValueError:
            print("Please enter a valid number.")


def make_list_of_free_fields(board):
    free = []
    for row in range(3):
        for col in range(3):
            if isinstance(board[row][col], int):
                free.append((row, col))
    return free


def victory_for(board, sign):
    for row in board:
        if all(cell == sign for cell in row):
            return True
    for col in range(3):
        if all(board[row][col] == sign for row in range(3)):
            return True
    if all(board[i][i] == sign for i in range(3)):
        return True
    if all(board[i][2-i] == sign for i in range(3)):
        return True
    return False


def draw_move(board):
    free = make_list_of_free_fields(board)
    if free:
        row, col = random.choice(free)
        board[row][col] = 'X'

# Initial board (computer plays first in middle)
board = [[1, 2, 3],
         [4, 'X', 6],
         [7, 8, 9]]

print("Welcome to Tic-Tac-Toe!")
display_board(board)

while True:
    enter_move(board)
    display_board(board)
    if victory_for(board, 'O'):
        print("You win!")
        break
    if not make_list_of_free_fields(board):
        print("It's a tie!")
        break

    print("Computer's move:")
    draw_move(board)
    display_board(board)
    if victory_for(board, 'X'):
        print("Computer wins!")
        break
    if not make_list_of_free_fields(board):
        print("It's a tie!")
        break
