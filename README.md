# tictactoe
import os
board = [
    ['_','_','_'],
    ['_','_','_'],
    ['_','_','_'],
]

def board_current_state():
    ref_grid = """
    1 2 3
    4 5 6
    7 8 9
    """
    grid = f"""
    {board[0][0]} {board[0][1]} {board[0][2]}
    {board[1][0]} {board[1][1]} {board[1][2]}
    {board[2][0]} {board[2][1]} {board[2][2]} 
    """
    print(ref_grid)
    print(grid)


def clear_screen():
    os.system('cls')


def take_input():
    position = input(" please enter the number between (1,9):")
    if int(position) > 9:
        print("please enter the number between (1,9):")   
    return int(position)


def player_name():        
    player1 = input("please enter your name")
    Player2 = input("please enter your name")
   


def play_game(player_name, position):
    if player_name == 1:
        sign = 'X'
    if player_name == 2:
        sign = '0'
    row = col = 0
    if position == 1 or position == 2 or position == 3:
        row = 0
    elif position == 4 or position == 5 or position == 6:
        row = 1
    elif position == 7 or position == 8 or position == 9:
        row = 2

    if position == 1 or position == 4 or position == 7:
        col = 0
    elif position == 2 or position == 5 or position == 8:
        col = 1
    elif position == 3 or position == 6 or position ==  9:
        col = 2
        print(play_game)
    # update the board
        board [row][col] = sign 


def is_gameover():
    #Horizantal match     
    player = None 
    if board[0][0] == board[0][1] == board [0][2]:
        player = board[0][0]
    elif board[1][0] == board[1][1] == board[1][2]:
        player = board[1][0]
    elif board[2][0] == board[2][1] == board[2][2]:
        player = board[2][0]

    #Vertical match 
    if board[0][0] == board[1][0] == board[2][0]:
        player = board[0][0]
    elif board[0][1] == board[1][1] == board[1][2]:
        player = board[0][1] 
    elif board[0][2] == board[1][2] == board[2][2]:
        player = board[0][2]

    #diagonal match
    if board [0][0] == board[1][1] == board[2][2]:
        player = board[0][0]
    elif board[1][2] == board[1][1] == board[2][0]:
        player = board[1][2]
    if player == 'X' or player =='0':
        return (True, player)
    else:
        return(False, None)


def main():
    num_of_plays = 0
    while num_of_plays < 9 :
#        clear_screen()
        board_current_state()
        position = take_input()
        if num_of_plays % 2 == 0:
            player = 1
        else:
            player = 2
        play_game(player,position)
        num_of_plays += 1
        gameover, won_player = is_gameover()
        if gameover == True:
            break

        if won_player == 'X':
            won_player = 'player1'
        elif won_player == '0':
            won_player = 'player2'

        board_current_state()
        if num_of_plays == 9:
            print("game Drawn")
        else:
            print(f"{won_player} Won")
main()








