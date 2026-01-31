# tictacto-game
we use python language for game
# Tic Tac Toe Game

board = ['1','2','3','4','5','6','7','8','9']
current_player = 'X'

def display_board():
    print()
    print(f" {board[0]} | {board[1]} | {board[2]} ")
    print("---|---|---")
    print(f" {board[3]} | {board[4]} | {board[5]} ")
    print("---|---|---")
    print(f" {board[6]} | {board[7]} | {board[8]} ")
    print()

def check_win():
    win_positions = [
        (0,1,2),(3,4,5),(6,7,8),
        (0,3,6),(1,4,7),(2,5,8),
        (0,4,8),(2,4,6)
    ]
    for a, b, c in win_positions:
        if board[a] == board[b] == board[c]:
            return True
    return False

turns = 0

while True:
    display_board()
    move = int(input(f"Player {current_player}, enter your move (1-9): "))

    if move < 1 or move > 9 or board[move-1] in ['X','O']:
        print("❌ Invalid move! Try again.")
        continue

    board[move-1] = current_player
    turns += 1

    if check_win():
        display_board()
        print(f"🎉 Player {current_player} wins!")
        break

    if turns == 9:
        display_board()
        print("🤝 It's a draw!")
        break

    current_player = 'O' if current_player == 'X' else 'X'
