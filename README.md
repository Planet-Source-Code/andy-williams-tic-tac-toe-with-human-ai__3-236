<div align="center">

## Tic Tac Toe with Human AI


</div>

### Description

The purpose for me was to create a simple game so that I could get exposure to Artifical Intellegence. I think I've suceeded in making a good bit of code with good, human like AI. I don't think you could find a more challenging player. If anyone can make this code shorter let me know.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Andy Williams](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/andy-williams.md)
**Level**          |Intermediate
**User Rating**    |2.6 (21 globes from 8 users)
**Compatibility**  |C\+\+ \(general\)
**Category**       |[Games](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/games__3-13.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/andy-williams-tic-tac-toe-with-human-ai__3-236/archive/master.zip)





### Source Code

```
/***************************************************************************
 *                                     *
 * ****  ****   ****  ****  ****    *    *     *    *
 * *  *  *  *  *  * *  * *  *   * *    * *   * *    *
 * ****  ****  *  * *    ****   *  *   * *  * *    *
 * *    * *  *  * * *** * *   *******   *  * *  *    *
 * *    *  *  *  * *  * *  *  *    *  *  *  *    *
 * *    *  *  ****  ****  *  * *    *  *     *    *
 *							  						            *
 ***************************************************************************
 * Program Name: *	  Tic Tac Toe         		  	  *
 ***************************************************************************
 *	File Name:	  *  TIC TAC TOE.CPP                  *
 ***************************************************************************
 *  Version:   *  1.0                        *
 ***************************************************************************
 *  Date:    *  12/29/998                     *
 ***************************************************************************
 *	Author:		  * 	Andrew Williams                  *
 ***************************************************************************
 *	Description  *  Tic tac toe, yet another copy of the ever popular  *
 *				  *  game                        *
 *   of     *                            *
 *         *                            *
 *  Program   *                            *
 ***************************************************************************/
/*=*=*=*=*=*=*=*=*=*=*=*=*=*=Include Directives*=*=*=*=*=*=*=*=*==*=*=*=*=*/
#include <iostream.h>
#include <string.h>
#include <iomanip.h>
#include <time.h>
#include <time.h> // for time in the random numbers
/*=*=*=*=*=*=*=*==*=*=*=*=*=*ProtoTypes*=*=*=*=*=*=*=*=*=*=*=*==*=*=*=*=*=*/
void init_mm( );
int number_range( int from, int to );
int number_mm( void );
void Print_Board();
typedef int CON;
CON Check_Won();
void Computers_Turn();
#define FALSE 0
#define TRUE  1
#define CAT  2
#define X_WON 3
#define O_WON 4
/*=*=*=*=*=*=*=*==*=*=*=*=*=*Constants*=*=*=*=*=*=*=*=*=*=*=*==*=*=*=*=*=*/
const int X = 1;
const int O = 2;
/*=*=*=*=*=*=*=*==*=*=*=*=*=*Global Variables*=*=*=*=*=*=*=*=*=*=*=*=*=*=*/
char The[4];
int x = 0, y = 0;
int Board[4][4] = { 0,0,0,0,
          0,0,0,0,
					0,0,0,0,
					0,0,0,0
					};
/*=*=*=*=*=*=*=*==*=*=*=*=*=*Main Function=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*/
void main()
{
	init_mm();
cout << "Welcome to Super Ultra Quazy Stellar Tic Tac Toe!\n"			<<
		"The Board is Numbered like this:\n"							<<
		"     0  1  2  \n"                   <<
		"           \n"                   <<
		"      |  |   \n"                   <<
		" 0   0,0|0,1|0,2  \n"										<<
		"    -------------- \n"                   <<
		" 1   1,0|1,1|1,2  \n"							  		<<
		"    -------------- \n"										<<
		" 2   2,0|2,1|2,2  \n"										<<
		"      |  |   \n"										<<
		"Press [Return] to Play\n"                   ;
cin.get(The, 4);
cin.ignore(80, '\n');
	while ( y != -1111 )
	{
		x = 0;
		y = 0;
		Print_Board();
		cout << "Enter the row number: ";
		cin >> x;
		cout << "\nEnter the column number: ";
		cin >> y;
		Board[x][y] = X;
		if( Check_Won() == CAT)
		{
			cout << "Cats Game!\n";
			Print_Board();
			return;
		}
		if( Check_Won() == X_WON)
		{
			cout << "You Won!\n";
			Print_Board();
			return;
		}
		if( Check_Won() == O_WON)
		{
			cout << "I Won!\n";
			Print_Board();
			return;
		}
		Computers_Turn();
		if( Check_Won() == CAT)
		{
			cout << "Cats Game!\n";
			Print_Board();
			return;
		}
		if( Check_Won() == X_WON)
		{
			cout << "You Won!\n";
			Print_Board();
			return;
		}
		if( Check_Won() == O_WON)
		{
			cout << "I Won!\n";
			Print_Board();
			return;
		}
	}
}
void Print_Board()
{
// some space
cout << '\n' << setw(5) << " " << setw(5) << "|" << setw(5) << " " << setw(5) << "|" << setw(5) << " " << setw(5) << "\n";
//First Square first row
if(Board[0][0] == X)
{
	cout << setw(5) << "X" << setw(5) << "|";
}
else if (Board[0][0] == O)
{
	cout << setw(5) << "O" << setw(5) << "|";
}
else
{
	cout << setw(5) << " " << setw(5) << "|";
}
//Second Square first row
if(Board[0][1] == X)
{
	cout << setw(5) << "X" << setw(5) << "|";
}
else if (Board[0][1] == O)
{
	cout << setw(5) << "O" << setw(5) << "|";
}
else
{
	cout << setw(5) << " " << setw(5) << "|";
}
//Third Square first row
if(Board[0][2] == X)
{
	cout << setw(5) << "X" << setw(5) << "\n";
}
else if (Board[0][2] == O)
{
	cout << setw(5) << "O" << setw(5) << "\n";
}
else
{
	cout << setw(5) << " " << setw(5) << "\n";
}
// some space
cout << setw(5) << " " << setw(5) << "|" << setw(5) << " " << setw(5) << "|" << setw(5) << " " << setw(5) << "\n";
//the horizontal line
cout << "______________________________\n";
// some space
cout << '\n' << setw(5) << " " << setw(5) << "|" << setw(5) << " " << setw(5) << "|" << setw(5) << " " << setw(5) << "\n";
//First Square Second Row
if(Board[1][0] == X)
{
	cout << setw(5) << "X" << setw(5) << "|";
}
else if (Board[1][0] == O)
{
	cout << setw(5) << "O" << setw(5) << "|";
}
else
{
	cout << setw(5) << " " << setw(5) << "|";
}
//Second Square Second Row The "Center" if you will
if(Board[1][1] == X)
{
	cout << setw(5) << "X" << setw(5) << "|";
}
else if (Board[1][1] == O)
{
	cout << setw(5) << "O" << setw(5) << "|";
}
else
{
	cout << setw(5) << " " << setw(5) << "|";
}
//Third Square Second Row
if(Board[1][2] == X)
{
	cout << setw(5) << "X" << setw(5) << "\n";
}
else if (Board[1][2] == O)
{
	cout << setw(5) << "O" << setw(5) << "\n";
}
else
{
	cout << setw(5) << " " << setw(5) << "\n";
}
// some space
cout << setw(5) << " " << setw(5) << "|" << setw(5) << " " << setw(5) << "|" << setw(5) << " " << setw(5) << "\n";
//the horizontal line
cout << "______________________________\n";
// some space
cout << '\n' << setw(5) << " " << setw(5) << "|" << setw(5) << " " << setw(5) << "|" << setw(5) << " " << setw(5) << "\n";
//First Square Third Row
if(Board[2][0] == X)
{
	cout << setw(5) << "X" << setw(5) << "|";
}
else if (Board[2][0] == O)
{
	cout << setw(5) << "O" << setw(5) << "|";
}
else
{
	cout << setw(5) << " " << setw(5) << "|";
}
//Second Square Third Row
if(Board[2][1] == X)
{
	cout << setw(5) << "X" << setw(5) << "|";
}
else if (Board[2][1] == O)
{
	cout << setw(5) << "O" << setw(5) << "|";
}
else
{
	cout << setw(5) << " " << setw(5) << "|";
}
//Third Square Third Row
if(Board[2][2] == X)
{
	cout << setw(5) << "X" << setw(5) << "\n";
}
else if (Board[2][2] == O)
{
	cout << setw(5) << "O" << setw(5) << "\n";
}
else
{
	cout << setw(5) << " " << setw(5) << "\n";
}
// some space
cout << setw(5) << " " << setw(5) << "|" << setw(5) << " " << setw(5) << "|" << setw(5) << " " << setw(5) << "\n\n";
}
CON Check_Won()
{
	// Across
	if( ( Board[0][0] == X && Board[0][1] == X && Board[0][2] == X ) ||
		( Board[1][0] == X && Board[1][1] == X && Board[1][2] == X ) ||
		( Board[2][0] == X && Board[2][1] == X && Board[2][2] == X ) ||
	//Down
		( Board[0][0] == X && Board[1][0] == X && Board[2][0] == X ) ||
		( Board[0][1] == X && Board[1][1] == X && Board[2][1] == X ) ||
		( Board[0][2] == X && Board[1][2] == X && Board[2][2] == X ) ||
	//Diag
		( Board[0][0] == X && Board[1][1] == X && Board[2][2] == X ) ||
		( Board[0][2] == X && Board[1][1] == X && Board[2][0] == X )  )
		return X_WON;
	// Across
	if(
		( Board[0][0] == O && Board[0][1] == O && Board[0][2] == O) ||
		( Board[1][0] == O && Board[1][1] == O && Board[1][2] == O) ||
		( Board[2][0] == O && Board[2][1] == O && Board[2][2] == O) ||
	//Down
		( Board[0][0] == O && Board[1][0] == O && Board[2][0] == O) ||
		( Board[0][1] == O && Board[1][1] == O && Board[2][2] == O) ||
		( Board[0][2] == O && Board[1][2] == O && Board[2][2] == O) ||
	//Diag
		( Board[0][0] == O && Board[1][1] == O && Board[2][2] == O) ||
		( Board[0][2] == O && Board[1][1] == O && Board[2][0] == O)
																		)
		return O_WON;
	if( Board[0][0] != 0 && Board[0][1] != 0 && Board[0][2] != 0 &&
		Board[1][0] != 0 && Board[1][1] != 0 && Board[1][2] != 0 &&
		Board[2][0] != 0 && Board[2][1] != 0 && Board[2][2] != 0 )
		return CAT;
	return FALSE;
}
void Computers_Turn()
{
//Can Computer Win now?
	//First Row
	if( Board[0][0] == O && Board[0][1] == O && Board[0][2] == 0)
	{
		Board[0][2] = O; return;
	}
	if( Board[0][2] == O && Board[0][1] == O && Board[0][0] == 0)
	{
		Board[0][0] = O; return;
	}
	if( Board[0][0] == O && Board[0][2] == O && Board[0][1] == 0)
	{
		Board[0][1] = O; return;
	}
	//Second Row
	if( Board[1][0] == O && Board[1][1] == O && Board[1][2] == 0)
	{
		Board[1][2] = O; return;
	}
	if( Board[1][2] == O && Board[1][1] == O && Board[1][0] == 0)
	{
		Board[1][0] = O; return;
	}
	if( Board[1][0] == O && Board[1][2] == O && Board[1][1] == 0)
	{
		Board[1][1] = O; return;
	}
	//Third Row
	if( Board[2][0] == O && Board[2][1] == O && Board[2][2] == 0)
	{
		Board[2][2] = O; return;
	}
	if( Board[2][2] == O && Board[2][1] == O && Board[2][0] == 0)
	{
		Board[2][0] = O; return;
	}
	if( Board[2][0] == O && Board[2][2] == O && Board[2][1] == 0)
	{
		Board[2][1] = O; return;
	}
	//First Column
	if( Board[0][0] == O && Board[1][0] == O && Board[2][0] == 0)
	{
		Board[2][0] = O; return;
	}
	if( Board[2][0] == O && Board[1][0] == O && Board[0][0] == 0)
	{
		Board[0][0] = O; return;
	}
	if( Board[0][0] == O && Board[2][0] == O && Board[1][0] == 0)
	{
		Board[1][0] = O; return;
	}
	//Second Column
	if( Board[0][1] == O && Board[1][1] == O && Board[2][1] == 0)
	{
		Board[2][1] = O; return;
	}
	if( Board[2][1] == O && Board[1][1] == O && Board[0][1] == 0)
	{
		Board[0][1] = O; return;
	}
	if( Board[0][1] == O && Board[2][1] == O && Board[1][1] == 0)
	{
		Board[1][1] = O; return;
	}
	//Third Column
	if( Board[0][2] == O && Board[1][2] == O && Board[2][2] == 0)
	{
		Board[2][2] = O; return;
	}
	if( Board[2][2] == O && Board[1][2] == O && Board[0][2] == 0)
	{
		Board[0][2] = O; return;
	}
	if( Board[0][2] == O && Board[2][2] == O && Board[1][2] == 0)
	{
		Board[1][2] = O; return;
	}
	//Diag
	if( Board[0][0] == O && Board[1][1] == O && Board[2][2] == 0)
	{
		Board[2][2] = O; return;
	}
	if( Board[2][2] == O && Board[1][1] == O && Board[0][0] == 0)
	{
		Board[0][0] = O; return;
	}
	if( Board[0][0] == O && Board[2][2] == O && Board[1][1] == 0)
	{
		Board[1][1] = O; return;
	}
	//Diag
	if( Board[0][2] == O && Board[1][1] == O && Board[2][0] == 0)
	{
		Board[2][0] = O; return;
	}
	if( Board[2][0] == O && Board[1][1] == O && Board[0][2] == 0)
	{
		Board[0][2] = O; return;
	}
	if( Board[2][0] == O && Board[0][2] == O && Board[1][1] == 0)
	{
		Board[1][1] = O; return;
	}
//Block X's Win
	//First Row
	if( Board[0][0] == X && Board[0][1] == X && Board[0][2] == 0)
	{
		Board[0][2] = O; return;
	}
	if( Board[0][2] == X && Board[0][1] == X && Board[0][0] == 0)
	{
		Board[0][0] = O; return;
	}
	if( Board[0][0] == X && Board[0][2] == X && Board[0][1] == 0)
	{
		Board[0][1] = O; return;
	}
	//Second Row
	if( Board[1][0] == X && Board[1][1] == X && Board[1][2] == 0)
	{
		Board[1][2] = O; return;
	}
	if( Board[1][2] == X && Board[1][1] == X && Board[1][0] == 0)
	{
		Board[1][0] = O; return;
	}
	if( Board[1][0] == X && Board[1][2] == X && Board[1][1] == 0)
	{
		Board[1][1] = O; return;
	}
	//Third Row
	if( Board[2][0] == X && Board[2][1] == X && Board[2][2] == 0)
	{
		Board[2][2] = O; return;
	}
	if( Board[2][2] == X && Board[2][1] == X && Board[2][0] == 0)
	{
		Board[2][0] = O; return;
	}
	if( Board[2][0] == X && Board[2][2] == X && Board[2][1] == 0)
	{
		Board[2][1] = O; return;
	}
	//First Column
	if( Board[0][0] == X && Board[1][0] == X && Board[2][0] == 0)
	{
		Board[2][0] = O; return;
	}
	if( Board[2][0] == X && Board[1][0] == X && Board[0][0] == 0)
	{
		Board[0][0] = O; return;
	}
	if( Board[0][0] == X && Board[2][0] == X && Board[1][0] == 0)
	{
		Board[1][0] = O; return;
	}
	//Second Column
	if( Board[0][1] == X && Board[1][1] == X && Board[2][1] == 0)
	{
		Board[2][1] = O; return;
	}
	if( Board[2][1] == X && Board[1][1] == X && Board[0][1] == 0)
	{
		Board[0][1] = O; return;
	}
	if( Board[2][1] == X && Board[0][1] == X && Board[1][1] == 0)
	{
		Board[1][1] = O; return;
	}
	//Third Column
	if( Board[0][2] == X && Board[1][2] == X && Board[2][2] == 0)
	{
		Board[2][2] = O; return;
	}
	if( Board[2][2] == X && Board[1][2] == X && Board[0][2] == 0)
	{
		Board[0][2] = O; return;
	}
	if( Board[0][2] == X && Board[2][2] == X && Board[1][2] == 0)
	{
		Board[1][2] = O; return;
	}
	//Diag
	if( Board[0][0] == X && Board[1][1] == X && Board[2][2] == 0)
	{
		Board[2][2] = O; return;
	}
	if( Board[2][2] == X && Board[1][1] == X && Board[0][0] == 0)
	{
		Board[0][0] = O; return;
	}
	if( Board[0][0] == X && Board[2][2] == X && Board[1][1] == 0)
	{
		Board[1][1] = O; return;
	}
	//Diag
	if( Board[0][2] == X && Board[1][1] == X && Board[2][0] == 0)
	{
		Board[2][0] = O; return;
	}
	if( Board[2][0] == X && Board[1][1] == X && Board[0][2] == 0)
	{
		Board[0][2] = O; return;
	}
	if( Board[2][0] == X && Board[0][2] == X && Board[1][1] == 0)
	{
		Board[1][1] = O; return;
	}
	int xx = 0, yy = 0, ok = 0, i = 0;
	xx = number_range(0, 2);
	yy = number_range(0,2);
	do
	{
		if( Board[xx][yy] == 0 )
		{
			Board[xx][yy] = O;
			break;
		}
		else
		{
			xx = number_range(0,2);
			yy = number_range(0,2);
			cout << "Thinking..." << endl;
		}
	}while ( i != -11);
}
/*
 * This is the Mitchell-Moore algorithm from Knuth Volume II.
 */
static	int	rgiState[2+55];
void init_mm( )
{
  int *piState;
  int iState;
  piState	= &rgiState[2];
  piState[-2]	= 55 - 55;
  piState[-1]	= 55 - 24;
  piState[0]	= ( (int) time( NULL ) ) & ( ( 1 << 30 ) - 1 );
  piState[1]	= 1;
  for ( iState = 2; iState < 55; iState++ )
  {
	piState[iState] = ( piState[iState-1] + piState[iState-2] )
			& ( ( 1 << 30 ) - 1 );
  }
  return;
}
int number_mm( void )
{
  int *piState;
  int iState1;
  int iState2;
  int iRand;
  piState		= &rgiState[2];
  iState1	 	= piState[-2];
  iState2	 	= piState[-1];
  iRand	 	= ( piState[iState1] + piState[iState2] )
			& ( ( 1 << 30 ) - 1 );
  piState[iState1]	= iRand;
  if ( ++iState1 == 55 )
	iState1 = 0;
  if ( ++iState2 == 55 )
	iState2 = 0;
  piState[-2]		= iState1;
  piState[-1]		= iState2;
  return iRand >> 6;
}
/*
 * Generate a random number.
 */
int number_range( int from, int to )
{
  int power;
  int number;
  if ( ( to = to - from + 1 ) <= 1 )
	return from;
  for ( power = 2; power < to; power <<= 1 )
	;
  while ( ( number = number_mm( ) & ( power - 1 ) ) >= to )
	;
  return from + number;
}
```

