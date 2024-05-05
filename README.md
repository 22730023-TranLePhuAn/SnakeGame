# SnakeGame
#include <iostream>
#include <conio.h>
#include <windows>
using namespace std;

bool gameOver;
const int height=20;
const int width=20;

int x,y,fruitX,fruitY,score;

int tailX[100],tailY[100],nTail;

enum eDirection {STOP=0, UP, DOWN, LEFT, RIGHT};
eDirection dir;

void Setup(){
    gameOver=false;
    dir=STOP:
    x=width/2;
    y=height/2;
    fruitX = rand() %width;
    fruitY = rand() %height;
}

void Draw(){
    
    system("CLS");
    
    for(int i=0;i<width;i++){
        cout<<"#";
    }cout<<endl;
    
    for(int i=0;i<height;i++){
        for(int j=0;j<width;j++){
            if(j==0 || j==width-1){
                cout<<"#";
            }else if(i==y && j==x){
                cout<<"O";
            }else if(i==fruitY && j==fruitX){
                cout<<"F";
            }else {
                
                bool print = false;
                
                for(in k=0;k<nTail;k++){
                    if(i==tailY[i] && j==tailX[i]){
                        cout<<"o";
                        print = true;
                    }
                }if(!print){cout<<" ";}
            }
        }cout<<endl;
    }
    
    for(int i=0;i<width;i++){
        cout<<"#";
    }cout<<endl;
    cout<<endl;
    cout<<"Score: "<<score<<endl;
}

void Input(){
    if(_khit()){
        switch(_getch()){
        case 'w':
            dir=UP;
            break;
        case 'a':
            dir=LEFT;
            break;
        case 's':
            dir=DOWN;
            break;
        case 'd':
            dir=RIGHT;
            break;
        default:
            break;
        }    
    }    
}

void Logic(){
    
    int prev = tailX[0];
    int prev = tailY[0];
    tailX[0]=x;
    tailY[0]=y;
    int prev2X,prev2Y;
    
    for(int i=1;i<nTail;i++){
        prew2X = tailX[i];
        prew2Y = tailY[i];
        tailX[i] = prevX;
        tailY[i] = prevY;
        prevX = prev2X;
        prevY = prev2Y;
    }
    
    switch(dir){
    case UP:
        y--;
        break;
    switch(dir){
    case DOWN:
        y++;
        break;
    switch(dir){
    case LEFT:
        x--;
        break;
    switch(dir){
    case RIGHT:
        x++;
        break;
    default:
        break;
    }
    
    if(x<0 || x>width || y<0 || y>height){
        gameOver=true;
    }
    
    for(int i=0;i<nTail;i++){
        if(x==tailX[i] && y==tailY[i]){
            gameOver=true;
        }
    }
    
    if(x==fruitX && y==fruitY){
        score+=10;
        fruitX = rand() %width;
        fruitY = rand() %height;
        nTail++;
    }
}

int main()
{
    Setup();
    while(!gameOver){
        Draw();
        Input();
        Logic();
        Sleep(40);
    }

    return 0;
}
