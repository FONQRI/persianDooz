
from tkinter import *
from tkinter import messagebox

import time
import sys
from  math import *
#*********************************Game Starter*********************************

root=Tk()
root.geometry('200x300+840+400')
root.config(background='#544854')
root.title( 'Game Start')
root.resizable(False,False)
StartLabel=Label(root,text='START',background='#81bd41',width = 20,heigh=3)
StartLabel.place(x = 20 , y = 100)
Mood = 0
def Mood1(event):
    global Mood 
    Mood = 1
    comming=Label(root,text ='Coming Soon' ,bg='#FFA500',width = 20,heigh=7)
    comming.place(x= 20, y = 100)
    def CLC(event):
        comming.place_forget()
    comming.bind('<1>',CLC)
    root.mainloop()
    #root.destroy()
def Mood2(event):
    global Mood
    Mood = 2
    root.destroy()
def Mood():
    SPL=Label(root,text='Single Player',bg='#81bd41',width = 20,heigh=3)#Single Player Label
    SPL.place(x=20, y=100)
    SPL.bind('<1>',Mood1)
    TPL=Label(root,text ='Two Player',background='#ff4040',width = 20,heigh=3)#Two Player Label
    TPL.place(x= 20, y = 153)
    TPL.bind('<1>',Mood2)
def SLC(event):#Start label callback
    StartLabel.place_forget()
    AboutLabel.place_forget()
    ExitLabel.place_forget()
    Mood()


    
StartLabel.bind('<1>',SLC)

logo=PhotoImage(file='Icon.png').subsample(6,6)
def ALC(event):# About Labe callback
    aboutwin=Toplevel(root)
    aboutwin.title('ABOUT')
    aboutwin.geometry('200x300+840+400')
    aboutwin.resizable(False,False)
    infoLabel=Label(aboutwin,text="I'm mr.Sabaghi Behnam i'm a python programmer and I have written itwith tkinter. It's open source and you can improv it if you like butmy name should be as first developeron this game .  ",
                    image = logo,background='#00c4cc',
                    foreground='#544854',
                    anchor=N,
                    wraplength=150)
    infoLabel.pack(fill=BOTH,expand=True)
    infoLabel.config(compound =TOP)


AboutLabel=Label(root,text='ABOUT',background='#00c4cc',width = 20,heigh=3)
AboutLabel.place(x = 20 , y = 153)
AboutLabel.bind('<1>',ALC)

def ELC(event):# About Labe callback
    root.destroy()
    sys.exit()
ExitLabel=Label(root,text='EXIT',background='#ff4040',width = 20,heigh=3)
ExitLabel.place(x = 20 , y = 206)
ExitLabel.bind('<1>',ELC)



def on_closing():
    if messagebox.askokcancel("Quit", "Do you want to quit?"):
        root.destroy()
        sys.exit()

root.protocol("WM_DELETE_WINDOW", on_closing)
root.mainloop()

boardary=list(range(15))
for x in range(15):
    boardary[x]=list(range(8))
for i in range(15):
    for j in range(8):
        boardary[i][j]=0
turn = 1
#**************************Main Board***************************************
class board():
    
    root=Tk()
    root.geometry('707x429')
    root.config(backgroun='#011820')
    root.title("Persian Dooz")
    root.resizable(False,False)
    blacktaw =PhotoImage(file='BlackTaw.png')
    orangetaw=PhotoImage(file='OrangeTaw.png')
    boardG=PhotoImage(file='BoardGame.png')
    boardcanvas=Canvas(root,width =707,height=429)
    boardcanvas.pack()
    boardcanvas.create_image(353,215,image=boardG)
    TI=boardcanvas.create_image(355,408,image=blacktaw)
    
    def winner():
        global boardary
        b= boardary
        for x in range(11):
            i = x+1
            for y in range(7):
                j= y+1
                if b[i][j]==turn and b[i + 1][j]==turn and b[i + 2][j]==turn and b[i + 3][j]==turn :
                    
                    return turn
        for x in range(11):
            i = x+1
            for y in range(4):
                j= y+1
                if b[i][j] == turn and b[i + 1][j + 1] == turn and b[i + 2][j + 2] == turn and b[i + 3][j + 3] == turn :
                    return turn
              
        for x in range(14):
            i = x+1
            for y in range(4):
                j= y+1
                if b[i][j] == turn and b[i][j + 1] == turn and b[i][j + 2] == turn and b[i][j + 3] == turn :
                    
                    return turn
        for x in range(11):
            i = 14 - x
            for y in range(4):
                j= y+1
                if b[i][j] == turn and b[i - 1][j + 1] == turn and b[i - 2][j + 2] == turn and b[i - 3][j + 3] == turn :
                    
                    return turn
        return 0
#********************************Classes***************************************

class Taw():
    def __init__(self ,turn,board):    
        self.turn = turn #color of Taw
        self.column = 1 #logical coulumn in game
        self.row = 0 #logical row in game
        if turn == 1:
            self.taw=board.boardcanvas.create_image(47,70,image=board.blacktaw)
        else:
            self.taw=board.boardcanvas.create_image(47,70,image=board.orangetaw)
        self.let=1
        self.done=0
    def moveLeft(self):
        
        if self.row==0 and self.let== 1:
            self.let=0
            if self.column > 1:
                self.column -= 1
                for x in range(47):
                    board.boardcanvas.move(self.taw, -1, 0) # <--- Use Canvas.move method.
                    board.root.update()
                    time.sleep(0.0010)
            #time.sleep(0.40)
            board.root.update()
            self.let=1
    def moveRight(self):
        if self.row==0 and self.let== 1:
            self.let=0
            if self.column <14:
                self.column += 1
                for x in range(47):
                    board.boardcanvas.move(self.taw, 1, 0) # <--- Use Canvas.move method.
                    board.root.update()
                    time.sleep(0.001)
            
            board.root.update()
            self.let=1
    def changeturn(self):
        global turn
        if turn == 1:
            turn = 2
            TI=board.boardcanvas.create_image(355,408,image=board.orangetaw)
        else:
            turn = 1
            TI=board.boardcanvas.create_image(355,408,image=board.blacktaw)
    def moveDown(self):
        global boardary
        global turn
        if self.row==0 and self.let == 1:
            if boardary[self.column][7] ==0:
                self.row = 7
                for x in range(56):
                    board.boardcanvas.move(self.taw, 0, 1)
                    time.sleep(0.001)
                    board.root.update()
                #time.sleep(0.40)
                for i in range(6):
                    if boardary[self.column][self.row - 1] ==0:
                    
                        self.row -=1
                        for j in range(40):
                            board.boardcanvas.move(self.taw, 0, 1)
                            board.root.update()
                            time.sleep(0.0005)
                        #time.sleep(0.40)
                        board.root.update()
                for x in range (  floor(((7-self.row)*47)/3)):
                    board.boardcanvas.move(self.taw,0 , -1)
                    board.root.update()
                    time.sleep(0.001)
                for x in range (  floor(((7-self.row)*47)/3)):
                    board.boardcanvas.move(self.taw,0 , 1)
                    board.root.update()
                    time.sleep(0.001)
                for x in range (  floor(((7-self.row)*47)/6)):
                    board.boardcanvas.move(self.taw,0 ,-1)
                    board.root.update()
                    time.sleep(0.001)
                for x in range (  floor(((7-self.row)*47)/6)):
                    board.boardcanvas.move(self.taw,0 ,1)
                    board.root.update()
                    time.sleep(0.001)
                boardary[self.column][self.row] = self.turn
                
                self.done = 1
                winner = board.winner()
                if winner != 0 :
                    board.root.destroy()
                    root=Tk()
                    root.title('Congratulation')
                    cafe=PhotoImage(file='cafe.png')
                    cafeboard=Canvas(root,width =707,height=429,bg='#000000')
                    cafeboard.pack()
                    l=Label(cafeboard,text ='Congratulations                                  you won     player {}'.format(turn)
                            ,background='#00c4cc',width = 30,heigh=5,anchor=CENTER
                            ,wraplength=250).place(x=220 , y=188)
                    cafeboard.create_image(353,215,image=cafe)
                    root.mainloop()
                    sys.exit()
                self.changeturn()
v =None



def TwoPlayerMood():
   
    global turn

    
    c = board()
    def on_closing():
        if messagebox.askokcancel("Quit", "Do you want to quit?"):
            board.root.destroy()
            sys.exit()

    board.root.protocol("WM_DELETE_WINDOW", on_closing)
    def make():
        global v
        v = Taw(turn,c)
    make()
    def right(event):
        v.moveRight()

    c.root.bind('<KeyPress-Right>',right)

    def left(event):
        v.moveLeft()
    
    c.root.bind('<KeyPress-Left>',left)
    def down(event):
        if v.row==0:
            v.moveDown()
            if v.done == 1:
                v.done= 0
                make()
        else :
            pass
    c.root.bind('<KeyPress-Down>',down)

#************************artificial intelligence*************************************************************


def make(c):
    # a fucaction for making new taw
    global v
    v = Taw(turn,c)

class AI():
    def __init__(self,c,v):
       v.changeturn()
       make(c)
    def check(boardary):
        ary= boardary
        

            
            
            



#********************************************Single Player****************************************************
def SinglePlayerMood():
    global turn
    if turn == 1:
        c = board()
        def on_closing():
            if messagebox.askokcancel("Quit", "Do you want to quit?"):
                board.root.destroy()
                sys.exit()
    
        board.root.protocol("WM_DELETE_WINDOW", on_closing)
        
        make(c)
        def right(event):
            v.moveRight()

        c.root.bind('<KeyPress-Right>',right)

        def left(event):
            v.moveLeft()
    
        c.root.bind('<KeyPress-Left>',left)

        
        def down(event):
            if v.row==0:
                v.moveDown()
                if v.done == 1:
                    v.done= 0
                    make(c)
                    ai=AI(c,v)
            else :
                pass
        c.root.bind('<KeyPress-Down>',down)

    
def main():
    if Mood == 2:
        TwoPlayerMood()
    else :
        SinglePlayerMood()
if __name__=='__main__':
    main()
