# Binus
code||sleep||repeat||
#creating a game called tick tock toe in the python#



#defining the global variable

board=["-","-","-",
       "-","-","-",
       "-","-","-"]
game=True

winner=None

current_player="x"


#defing the display board function
def display_board():
    print(board[0]+ "|"+ board[1]+ "|"+ board[2])
    print(board[3]+ "|"+ board[4]+ "|"+ board[5])
    print(board[6]+ "|"+ board[7]+ "|"+ board[8])
    
    #while the game is still gonig on



    
#defing the play game function    
def play_game():
    display_board()
    
    while game:
         
            handle_turn(current_player)
            
            check_if_game_over()
            
            flip_player()
    if(winner == "x" or winner == "o"): 
                print(winner +""+""+ "won.");
    elif(winner == None):
                print(" tie")
        
#defing the handle turn fuction    
def handle_turn(player):
    print(player + "   turn.")
    position=input("choose a number betweeen 1 to 9:-   ")
    
    valid=False
    while not valid:
    
        while position not in ["1","2","3","4","5","6","7","8","9"]:
             position=input("invalid input .choose a number betweeen 1 to 9:-   ")
        position=int(position)-1
    
        if board[position] =="-":
             valid=True
     
        else:
             print("you cannot go over there move on buddy")
      
        
    board[position] = player
    display_board()    
#defing the game over fuction    
def check_if_game_over():
    check_if_win()
    check_if_tie()
    
    
    
    
#defining the function check  for winner    
def check_if_win():
    
    global winner
    
    row_winner=check_rows()
    
    column_winner=check_columns()
    
    diagonal_winner=check_diagonals()
    
    if row_winner:
        winner=row_winner
    elif column_winner:
        winner=column_winner
    elif diagonal_winner:
        winner=diagonal_winner
    else:
        winner=None
        return
    
#defining the fuction check if tie
def check_if_tie():
    #check rows
    #check columns
    #check diagonals
    global game
    if "-" not in board:
        game=False
    return


#defining the fuction check diagonals
def check_rows():
    global game
    row_1 = board[0]==board[1]==board[2] !="-"
    row_2 = board[3]==board[4]==board[5] !="-"
    row_3 = board[6]==board[7]==board[8] !="-"
    
    if row_1 or row_2 or row_3:
        game=False
    if row_1:
        return board[0]
    if row_2:
        return board[3]
    if row_3:
        return board[6]
        return
    return




#defining the fuction check diagonals
def check_columns():
    global game
    columns_1 = board[0]==board[3]==board[6] !="-"
    columns_2 = board[1]==board[4]==board[7] !="-"
    columns_3 = board[2]==board[5]==board[8] !="-"
    
    if columns_1 or columns_2 or columns_3:
        game=False
    if columns_1:
        return board[0]
    if columns_2:
        return board[1]
    if columns_3:
        return board[2]
        return
    return

#defining the fuction the check diagonals
def check_diagonals():
    global game
    diagonal_1 = board[0]==board[4]==board[8] !="-"
    diagonal_2 = board[6]==board[4]==board[2] !="-"
    
    if diagonal_1 or diagonal_2:
        game=False
    if diagonal_1:
        return board[0]
    if diagonal_2:
        return board[6]
        return
    return
#defining the fuctions check player
def flip_player():
    global current_player
    
    if current_player=="x":
        current_player="o"
    elif current_player=="o":
        
        current_player="x"
    return

play_game()
