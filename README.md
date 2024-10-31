# Tic-Tac-Toe
code for Tic-Tac-Toe

#include<stdio.h>
#include<conio.h>

void Grid(char *block);
int Check();
void system();
int checkValidity(char *block,int position);

int main()
{
    char block[]={'0','1','2','3','4','5','6','7','8','9'};
    
    int position;  // Store the position at which you want to enter X or O .
    int chance= 1;  // for selection of Turn and Mark.
    while(1)
    {
        int player= (chance % 2 != 0) ? 1 : 2;
        char Mark = (chance % 2 != 0) ? 'X' : 'O' ;
        Grid(block);
        printf("Enter Position Player %d : ",player);
        scanf("%d",&position);
        if(position < 1 || position > 9)
        {
            printf("Invalid Position !!!");
            break ;
        }
        int ValidityResult = checkValidity(block,position);
        if (ValidityResult == 0){
            printf("Invalid Postion, Already Taken ...Choose Other\n");
            printf("Enter any Key to Continue ...\n");
            getch();
            continue;
        }
        
        block[position] = Mark;
        Grid(block);
        chance++;
        int Result = Check(block);
        if(Result == 1)
        {
            printf("\nPlayer %d is a Winner .",player);
            break;
        }
        if(Result == 0)
        {
            printf(" \n***MATCH DRAW***.");
            break;
        }
        if(Result == -1)
        {
            continue;
        }
    }

    return 0;
}

void Grid(char *block)
{
    system("cls");
    printf("#TIC-TAC-TOE#\n");
    printf("    |    |    \n");
    printf(" %c  | %c  | %c \n",block[1],block[2],block[3]);
    printf("____|____|____\n");
    printf("    |    |    \n");
    printf(" %c  | %c  | %c \n",block[4],block[5],block[6]);
    printf("____|____|____\n");
    printf("    |    |    \n");
    printf(" %c  | %c  | %c \n",block[7],block[8],block[9]);
    printf("    |    |    \n");
}

int Check(char *block)
{
    if(block[1] == block[2] && block[2] == block[3]) return 1;
    if(block[4] == block[5] && block[5] == block[6]) return 1;
    if(block[7] == block[8] && block[8] == block[9]) return 1;
    if(block[1] == block[4] && block[4] == block[7]) return 1;
    if(block[2] == block[5] && block[5] == block[8]) return 1;
    if(block[3] == block[6] && block[6] == block[9]) return 1;
    if(block[1] == block[5] && block[5] == block[9]) return 1;
    if(block[3] == block[5] && block[5] == block[7]) return 1;

    int count=0;
    for(int i=1;i<=9;i++)
    {
        if(block[i] == 'X' || block[i] == 'O') count++;
    }

    if(count == 9) return 0;

    return -1;
    
}

int checkValidity(char *block,int position)
{
    if(block[position] == 'X' || block[position] == 'O') return 0;
   
}
