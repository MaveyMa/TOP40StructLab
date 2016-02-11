//Name: Mavey Ma
//Created: Friday, February 5, 2016
//Top 40 Struct Lab

#include<iostream>
#include<string> //getline(), substr()
#include<fstream> //ifstream, ofstream
#include<cstdlib> //exit()
using namespace std;

struct Song {
	string songTitle;
	string artist;
};

void initSongs(ifstream& inputFile, Song arr[ ], unsigned int arrSize);
void displaySongs(Song arr[ ], unsigned int arrSize);
void searchForSongsByArtist(Song arr[], unsigned int arrSize, string artist);
Song searchForSongByTitle(Song arr[], unsigned int arrSize, string title);
char menu();

int main()
{
	ifstream fin;

	const int SIZE = 40;
	Song arrayA[SIZE];
	Song info;
	char choice;
	string inputArtist, inputTitle;
	bool repeat = true;

	fin.open("top40.txt");
	if (fin.fail())
	{
		cout << "ERROR. CANNOT OPEN FILE.\n";
		exit(1);
	}//END FAIL CHECK

	initSongs(fin, arrayA, SIZE);

	while (repeat)
	{
		choice = menu();
		choice = toupper(choice); //AVOID CASE SENSITIVITY

		switch (choice)
		{
			case 'D':
				cout << "---------------------" << endl;
				displaySongs(arrayA, SIZE);
				break;
			//EXITS PROGRAM, NO OUTPUT
			case 'S':
				cout << "---------------------" << endl;
				cout << "Enter artist name: ";
				cin.clear();
				cin.ignore(); //CLEARS THE BUFFER
				getline(cin, inputArtist);
				searchForSongsByArtist(arrayA, SIZE, inputArtist);
				break;
			case 'T':
				cout << "Enter song name: ";
				cin >> inputTitle;
				info = searchForSongByTitle(arrayA, SIZE, inputTitle);
				cout << info.artist << endl;
				cout << info.songTitle << endl;
				break;
			case 'Q':
				repeat = false;
				break;
			default:
				cout << "Should never reach here.\n";
				break;
		}//END SWITCH
		cout << "---------------------" << endl;
	}//END REPEAT LOOP
	//displaySongs(arrayA, SIZE);
	//searchForSongsByArtist(arrayA, SIZE, "Justin Bieber");
	/*info = searchForSongByTitle(arrayA, SIZE, "Stressed Out");
	cout << info.artist << endl;
	cout << info.songTitle << endl;*/

	fin.close();
	return 0;
}//END MAIN

char menu()
{
	char ans;
	cout << "D --- Display top 40 songs." << endl;
	cout << "S --- Search song by artist." << endl;
	cout << "T --- Search song by title." << endl;
	cout << "Q --- Quit program." << endl;
	cout << "Enter choice: ";
	cin >> ans;

	return ans;
}//END MENU

void initSongs(ifstream& inputFile, Song arr[ ], unsigned int arrSize)
{
	for (int i=0; i<arrSize; i++)
	{
		getline(inputFile, arr[i].artist);
		getline(inputFile, arr[i].songTitle);
	}
	for (int i=0; i<arrSize-1; i++)
	{
		arr[i].artist = arr[i].artist.substr(0, arr[i].artist.length()-1);
		arr[i].songTitle = arr[i].songTitle.substr(0, arr[i].songTitle.length()-1);
	}
	return;
}//END INIT SONGS

void displaySongs(Song arr[ ], unsigned int arrSize)
{
	for (int i=0; i<arrSize; i++)
	{
		cout << arr[i].artist << endl;
		cout << arr[i].songTitle << endl;
	}
	return;
}//END DISPLAY SONGS

void searchForSongsByArtist(Song arr[], unsigned int arrSize, string artist)
{
	for (int i=0; i<arrSize; i++)
	{
		if (arr[i].artist == artist)
		{
			cout << arr[i].songTitle << endl;
		}
	}
	return;
}//END SEARCH BY ARTIST NAME

Song searchForSongByTitle(Song arr[], unsigned int arrSize, string title)
{
	for (int i=0; i<arrSize; i++)
	{
		if (arr[i].songTitle == title)
		{
			return arr[i];
		}
	}
}//END SEARCH BY SONG TITLE
