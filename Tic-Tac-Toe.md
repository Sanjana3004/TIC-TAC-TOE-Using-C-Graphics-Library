# TIC-TAC-TOE-Using-C-Graphics-Library
  COMPILER: Turbo C 2.01
   

#include <stdio.h>
#include <graphics.h>
#include <stdlib.h>
#include <conio.h>
int rowcol[9]={1,2,3,4,5,6,7,8,9};

void main(){

int gdriver,gmode,errorcode;
int is;
int i,temp;
int bool;
char ch[2];
bool=0;
gdriver=EGA;
gmode=EGAHI;
/initialize the graphics driver/
initgraph(&gdriver,&gmode,"");
/* error handling for graphics driver */
errorcode = graphresult();
if ( errorcode != grOk ) {
printf("Graphics Error \n %s",grapherrormsg(errorcode));
printf("\n Press any key to halt:");
getch();
exit(1);
}

setbkcolor(11);
setcolor(1);
settextstyle(0,0,2);
outtextxy(40,40,"WELCOME TO THE GAME OF SUNCHOKRI");
/*
for(is=1000;is>500;is--){
sound(is);
delay(250);
}
nosound();
*/
setcolor(12);

outtextxy(150,120,"BY SOMDUTT GANGULY");
/* preloader logic in c programming */
setcolor(1);
i=0;
while(i!=600){
preloader(i);
delay(300);
i++;
}


sleep(2);
cleardevice();
mainscreen();
positionofx();
chanceofplayer(bool);

/*if q is pressed quit the game */
while((*ch=getch())!='q') {
/if n is pressed new game/
	if(*ch=='n'){
		for(is=0;is<9;is++){
		rowcol[is]=is+1;
			}
		bool=0;
		cleardevice();
		mainscreen();
		positionofx();
		chanceofplayer(bool);
		}

		temp=atoi(ch) ;
	if (temp==0){
		}
	else {

	if (rowcol[temp-1]==11 || rowcol[temp-1]==22){
	}
	else {
	if(bool==0){
	rowcol[temp-1]=11;
	}
	else
	{
	rowcol[temp-1]=22;
	}
	cleardevice();
	mainscreen();
	positionofx();
	if(bool==0){
	bool=1;
	}
	else
	{
	bool=0;
	}
	chanceofplayer(bool);
	}
	}
	}
/*
getch(); */
/closing or deallocating graphic driver/
closegraph();
}

/main background screen/
mainscreen() {
setbkcolor(12);
rectangle(10,10,620,250);
setcolor(14);
settextstyle(0,0,4);
outtextxy(35,300,"S U N C H O K R I");
setcolor(9);
settextstyle(0,0,2);
outtextxy(105,220,"Player 1 :11 Player 2 :22");
setcolor(15);
settextstyle(0,0,1);
outtextxy(0,0,"Author: Somdutt Ganguly - gangulysomdutt@yahoo.com - Apr 2003");
/* small rectagle for sunchokri..   */
setcolor(WHITE);
rectangle(20,20,300,200);
	rectangle(50,50,90,80);
	rectangle(100,50,140,80);
	rectangle(150,50,190,80);

	rectangle(50,120,90,90);
	rectangle(100,120,140,90);
	rectangle(150,120,190,90);

	rectangle(50,160,90,130);
	rectangle(100,160,140,130);
	rectangle(150,160,190,130);


	outtextxy(399,60,"q TO QUIT GAME");
	outtextxy(399,80,"n FOR NEW GAME");



}





/* logic of various functions in c */
preloader(int i) {

outtextxy(i,300,"|");

}

positionofx(){
char x[10];
setcolor(YELLOW);

	itoa(rowcol[8],x,10);
	/*last row */
	outtextxy(165,140,x);
	itoa(rowcol[7],x,10);
	outtextxy(115,140,x);
	itoa(rowcol[6],x,10);
	outtextxy(65,140,x);

	/*second last row */
	itoa(rowcol[5],x,10);
	outtextxy(165,100,x);
	itoa(rowcol[4],x,10);
	outtextxy(115,100,x);
	itoa(rowcol[3],x,10);
	outtextxy(65,100,x);

	/*first row */
	itoa(rowcol[2],x,10);
	outtextxy(165,60,x);
	itoa(rowcol[1],x,10);
	outtextxy(115,60,x);
	itoa(rowcol[0],x,10);
	outtextxy(65,60,x);
}

 chanceofplayer(int bool1 ) {
 char s[1];
 if(bool1==0){
 bool1=1; }
 else
 {
 bool1=2; }

 itoa(bool1,s,10);
 setcolor(4);
 outtextxy(33,33,"Turn of player : ");
 outtextxy(173,33,s);

 /* logic for winning the game */
 if((rowcol[0]==11 && rowcol[1]==11 && rowcol[2]==11)||(rowcol[3]==11 && rowcol[4]==11 && rowcol[5]==11)||(rowcol[6]==11&&rowcol[7]==11&&rowcol[8]==11)||(rowcol[0]==11&&rowcol[4]==11&&rowcol[8]==11)||(rowcol[2]==11&&rowcol[4]==11&&rowcol[6]==11)){
 outtextxy(399,100, "1 WINS");
 sound(350);
 delay(2000);
 nosound();
 }
 else if((rowcol[0]==22&&rowcol[1]==22&&rowcol[2]==22)||(rowcol[3]==22&&rowcol[4]==22&&rowcol[5]==22)||(rowcol[6]==22&&rowcol[7]==22&&rowcol[8]==22)||(rowcol[0]==22&&rowcol[4]==22&&rowcol[8]==22)||(rowcol[2]==22&&rowcol[4]==22&&rowcol[6]==22)){
 outtextxy(399,100, "2 WINS");
 sound(350);
 delay(2000);
 nosound();
 }
 else if((rowcol[0]==22&&rowcol[3]==22&&rowcol[6]==22)||(rowcol[1]==22&&rowcol[4]==22&&rowcol[7]==22)||(rowcol[2]==22&&rowcol[5]==22&&rowcol[8]==22)){
 outtextxy(399,100, "2 WINS");
 sound(350);
 delay(2000);
 nosound();
 }
else if((rowcol[0]==11&&rowcol[3]==11&&rowcol[6]==11)||(rowcol[1]==11&&rowcol[4]==11&&rowcol[7]==11)||(rowcol[2]==11&&rowcol[5]==11&&rowcol[8]==11)){
 outtextxy(399,100, "1 WINS");
 sound(350);
 delay(2000);
 nosound();
 }
 else{
 outtextxy(399,100,"NO RESULT");
 }
 }
