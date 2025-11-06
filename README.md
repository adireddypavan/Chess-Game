# Chess-Game

using python program developed chess game

# Step 1: Define the board
def initialize_board():
    board = [
        ["r", "n", "b", "q", "k", "b", "n", "r"],
        ["p"] * 8,
        [" "] * 8,
        [" "] * 8,
        [" "] * 8,
        [" "] * 8,
        ["P"] * 8,
        ["R", "N", "B", "Q", "K", "B", "N", "R"]
    ]
    return board

# Step 2: Display the board
def print_board(board):
    print("  a b c d e f g h")
    for i, row in enumerate(board):
        print(8 - i, " ".join(row), 8 - i)
    print("  a b c d e f g h")

# Step 3: Move pieces
def move_piece(board, start, end):
    start_row, start_col = 8 - int(start[1]), ord(start[0]) - ord('a')
    end_row, end_col = 8 - int(end[1]), ord(end[0]) - ord('a')
    piece = board[start_row][start_col]
    board[end_row][end_col] = piece
    board[start_row][start_col] = " "

# Step 4: Main game loop
def play_chess():
    board = initialize_board()
    print_board(board)
    while True:
        move = input("Enter your move (e.g., e2 e4): ")
        if move.lower() == "exit":
            break
        try:
            start, end = move.split()
            move_piece(board, start, end)
            print_board(board)
        except Exception as e:
            print("Invalid move. Try again.")

# Run the game
play_chess()
