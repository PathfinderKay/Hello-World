# Hello-World
Github Trainning + small program

Display and move the cursor

#include <stdio.h>  //appel printf()
#include <stdlib.h> //appel rand(), srand()
#include <time.h>   //appel time()
#include <conio.h>> // appel kbhit(), getch()
#include <windows.h> //appel gotoxy()

void gotoxy(int x, int y)  
{
    COORD c;

    c.X=x;
    c.Y=y;

    SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE), c);
}

void textcolor(int color) 
{
    SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), color);
}

int main()
{
 int touch=0, fin=0, res, x, y;
    const int TX=77, TY=22;

    // Player
    srand(time(NULL));
    x=rand()%TX;
    y=rand()%TY;

    textcolor(12);
    gotoxy(x, y);
    putchar('X');

    while (!fin)
    {
        if (kbhit())
        {
            gotoxy(x, y);
            putchar(' ');

            res=getch();

            switch (res)
            {
                case 72: y--;   break;         //case 'z': y--;   break;
                case 77: x++;   break;         //case 'd': x++;   break;
                case 80: y++;   break;         //case 's': y++;   break;
                case 75: x--;   break;         //case 'q': x--;   break;
                case 224:       break;
                default: fin=1; break;
            }

            if (x<0)
                x=TX;
            if (x>TX)
                x=0;
            if (y<0)
                y=TY;
            if (y>TY)
                y=0;

            gotoxy(x, y);
            putchar('X');
        }
    }

    return 0;
}
