# Tic-Tac-Toe-Game
Develop a two-player text-based Tic-Tac-Toe game
def print_board(board):
    for row in board:
        print(" ".join(row))
    print()

def check_winner(board, player):
    # Check rows, columns, and diagonals for a win
    for i in range(3):
        if all(cell == player for cell in board[i]) or all(board[j][i] == player for j in range(3)):
            return True
    if all(board[i][i] == player for i in range(3)) or all(board[i][2 - i] == player for i in range(3)):
        return True
    return False

def tic_tac_toe():
    board = [[' ' for _ in range(3)] for _ in range(3)]
    players = ['X', 'O']
    current_player = players[0]

    print("Welcome to Tic-Tac-Toe!")
    print_board(board)

    for _ in range(9):
        row = int(input("Enter row (0, 1, or 2): "))
        col = int(input("Enter column (0, 1, or 2): "))

        if board[row][col] == ' ':
            board[row][col] = current_player
            print_board(board)

            if check_winner(board, current_player):
                print(f"Player {current_player} wins!")
                break

            current_player = players[1] if current_player == players[0] else players[0]
        else:
            print("Cell already occupied. Try again.")

    print("Game Over!")

tic_tac_toe()
