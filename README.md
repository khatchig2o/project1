#include <iostream>

using namespace std;
char current_marker;
int current_player;

char board[3][3] = { {'1','2','3'},{'4','5','6'},{'7','8','9'} };

void drawboard()
{
	
	cout << "\t\t" << board[0][0] << " | " << board[0][1] << " | " << board[0][2] << " " << endl;
	cout << "\t       _ _ _ _ _ _  \n";
	cout << "\t\t" << board[1][0] << " | " << board[1][1] << " | " << board[1][2] << " " << endl;
	cout << "\t       _ _ _ _ _ _  \n";
	cout << "\t\t" << board[2][0] << " | " << board[2][1] << " | " << board[2][2] << " " << endl;
}

void placemarker(int slot)
{
	int col;
	int row;
	row = slot / 3;
	if (slot % 3 ==0)
	{
		row = row - 1;
		col = 2;
	}
	else
	{
		col = (slot % 3) - 1;
	}
	board[row][col] = current_marker;

}

char  winner()
{
	for (int i = 0; i < 3; i++)
	{
		//row 
		if (board[i][0] == board[i][1] && board[i][1] == board[i][2])
		{
			return current_player;
		}
		//colume
		else if (board[0][i] == board[1][i] && board[1][i] == board[2][i])
		{
			return current_player;
		}
	}
		if (board[0][0] == board[1][1] && board[1][1] == board[2][2])
		{
			return current_player;
		}
		if (board[0][2] == board[1][1] && board[1][1] == board[2][0])
		{
			return current_player;
		}
		else
		{
			return 0;
		}
}

void swap()
{
	if (current_marker == 'x')
	{
		current_marker = 'o';
	}
	else
	{
		current_marker = 'x';
	}

	if (current_player == '1')
	{
		current_player = '2';
	}
	else
	{
		current_player = '1';
	}

}

void game()
{
	char marker_p1;
	int slot;
	int player_wone;
	cout << " Player one choos your marker :";
	cin >> marker_p1;

	current_player = 1;
	current_marker = marker_p1;

	drawboard();

	for (int i = 0; i < 9; i++)
	{

		cout << " Its player " << current_player << "'s turn .Enter your slot :";
		cin >> slot;

		placemarker(slot);
		player_wone = winner();
		swap();

		drawboard();
	}
}

int main()
{
	game();
}
