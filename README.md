from tkinter import *

w =Tk()
w.title('Tic Tok Toe Game')
#w.geometry('700x700')

def callback(r,c):
    global player
    if player =="X" and state[r][c]==0 and stop_game== False:
        b[r][c].config(text="X",fg='black',bg='white')
        state[r][c]="X"
        player = "O"

    if player =="O" and state[r][c]==0 and stop_game== False:
        b[r][c].config(text="O",fg='black',bg='white')
        state[r][c]="O"
        player = "X"

    check_winner()

def check_winner():
    global stop_game
    for i in range(3):
        if state[i][0]==state[i][1]==state[i][2]!=0:
            b[i][0].config(bg='light green')
            b[i][1].config(bg='light green')
            b[i][2].config(bg='light green')
            stop_game= True
    for i in range(3):

        if state[0][i]==state[1][i]==state[2][i]!=0:
            b[0][i].config(bg='light green')
            b[1][i].config(bg='light green')
            b[2][i].config(bg='light green')
            stop_game= True

        if state[0][0]==state[1][1]==state[2][2]!=0:
            b[0][0].config(bg='light green')
            b[1][1].config(bg='light green')
            b[2][2].config(bg='light green')
            stop_game= True

        if state[0][2]==state[1][1]==state[2][0]!=0:
            b[0][2].config(bg='light green')
            b[1][1].config(bg='light green')
            b[2][0].config(bg='light green')
            stop_game= True             
b = [[0,0,0],
     [0,0,0],
     [0,0,0]]

state = [[0,0,0],
         [0,0,0],
         [0,0,0]]

for i in range(3):
    for j in range(3):
        b[i][j]= Button(font=("Arial",60),width=4,bg='light pink',command= lambda r=i,c=j:callback(r,c))
        b[i][j].grid(row=i,column=j)
player ="X"
stop_game = False
mainloop()
