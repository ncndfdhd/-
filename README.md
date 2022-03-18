#include<stdio.h>
#include<windows.h>
#include<string.h>
#include<conio.h>
#define H 9
#define L 11
char a[H][L+1]={
	{"*#*********"},
	{"***###*###*"},
	{"###**#****#"},
	{"*#**###**#*"},
	{"***********"},
    {"#####*##*##"},
	{"**#*****#*E"},
    {"***#*###**#"},
	{"*#*********"},
    };
void map()
{
	for(int i=0;i<H;i++)
    {
    	puts(a[i]);
	}	
}
void show_cursor(int x,int y)
{
	COORD pos;
	pos.X=x;
	pos.Y=y;
	printf("curX=%d,curY=%d\n",x,y);
	SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE),pos);
}
int curX,curY;
int main()
{
	while(1)
	{
		system("cls");
	   map();
       show_cursor(curX,curY);
       char t=getch();	
       if(t=='w')
       {
       	if((curY-1)>=0&&(a[curY-1][curX]=='*'||a[curY-1][curX]=='E'))
       	curY--;
	   }
	   else if(t=='s')
	   {
	   	if((curY+1)<=H&&(a[curY+1][curX]=='*'||a[curY+1][curX]=='E'))
	   	curY++;
	   }
	   else if(t=='a')
	   {
	   	if((curX-1)>=0&&(a[curY][curX-1]=='*'||a[curY][curX-1]=='E'))
	   	curX--;
	   }
	   else 
	   {
	   	if(t=='d')
	   	{
	   		if((curX+1)<=L&&(a[curY][curX+1]=='*'||a[curY][curX+1]=='E'))
	   	curX++;
		   }
	   }
	   if(a[curY][curX]=='E') 
	      break;
	 } 
	 printf("\n恭喜走出迷宫"); 
	return 0;
 } # -
