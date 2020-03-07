#include <iostream>
#include <string>
using namespace std;

class Connect4 {
public:

	char** p; int s; bool stop;

	Connect4() : p(0), s(0), stop(false) { 
		system("CLS");
	}

	~Connect4() {
		for (int i = 0; i < s; i++) {
			delete p[i];
		}
		delete p;
	}

	bool Init(int l) {
		if (l < 4 || l > 11) {
			cout << "invalid size: " << l << endl;
			return false;
		}
		s = l;
		setsize();
		return true;
	}


	void Display() {

		cout << " "; for (int i = 0; i < s; i++) cout << (i + 1) << '\t';
		cout << endl;
		cout << " "; for (int i = 0; i < s; i++) cout << "-" << '\t'; 		cout << endl;
		for (int i = s - 1; i >= 0; --i) { cout << " "; for (int j = 0; j < s; j++) cout << p[i][j] << '\t'; cout << endl; }
		cout << " "; for (int i = 0; i < s; i++) cout << "-" << '\t';
		cout << endl;
	}
	bool setAr(int choice, int var) {



		for (int c = 0; c < s; c++) {
			char& C = *(p[c] + choice - 1);
			if (C == '0') { C = var + 48; return true; }
		}
		return false; 
	}
	bool checkwin(int va) {
		for (int y = 0; y < s; y++) {
			for (int x = 0; x < s; x++) {
				if ((x < s - 3 && p[x][y] == p[x + 1][y] && p[x + 1][y] == p[x + 2][y] && p[x + 2][y] == p[x + 3][y] && p[x + 3][y] == va + 48) //check left to right (horizontal) winner
					|| (y < s - 3 && p[x][y] == p[x][y + 1] && p[x][y + 1] == p[x][y + 2] && p[x][y + 2] == p[x][y + 3] && p[x][y + 3] == va + 48) //check bottom to top (vertical) winner
					|| (x < s - 3 && y < s - 3 && p[x][y] == p[x + 1][y + 1] && p[x + 1][y + 1] == p[x + 2][y + 2] && p[x + 2][y + 2] == p[x + 3][y + 3] && p[x + 3][y + 3] == va + 48) //check bottom left to top right (diagonal) winner
					|| (x > 2 && y < s - 3 && p[x][y] == p[x - 1][y + 1] && p[x - 1][y + 1] == p[x - 2][y + 2] && p[x - 2][y + 2] == p[x - 3][y + 3] && p[x - 3][y + 3] == va + 48)) { //bottom right to top left (diagonal) winner
					cout << "Player " << va << " won " << endl << "Enter 0 to exit or 1 to play again" << endl;
					if (!getEndChoice()) {
						stop = true; // 
					}
					return true;
				}
			}
		}
		int tie = 0;
		for (int x = 0; x < s; x++)
			tie += (p[x][s - 1] != '0');
		if (tie == s) {
			cout << "Game ended...its a draw" << endl << "Enter 0 to exit or 1 to play again" << endl;
			if (!getEndChoice()) {
				stop = true;
			}
			return true;
		}
		return false;
	}
private:
	bool getEndChoice() {
		int choice = -1;
		while (1) {
			cin >> choice;
			if (choice == 0) return false;
			if (choice == 1) return true;
		}
	}

	void setarr() {
		for (int y = 0; y < s; y++) {
			for (int x = 0; x < s; x++) {
				p[x][y] = '0';
			}
		}
	}
	void setsize() {
		p = new char* [s];
		for (int i = 0; i < s; i++)
			p[i] = new char[s];
		setarr();
	}

};

int main() {
	Connect4 obj; int choice, l; int check = 0;
	do {
		check = 1;
		cout << "Enter the size of Game (x*x): "; cin >> l;
		
	} while (!obj.Init(l));
	system("CLS");
	obj.Display();

	while (!obj.stop) {
		for (int i = 1; i <= 2; i++)
		{
			cout << "Player " << i << " enter choice: "; cin >> choice;
			if (!obj.setAr(choice, i)) {
				system("CLS");
				obj.Display();
				cout << "This column is filled. Please choose again" << endl;
				i--;
			}
			system("CLS");
			obj.Display();
			if (obj.checkwin(i)) { 
				obj.Init(l);
				system("CLS");
				obj.Display();
				break;
			}
		}
	}
	system("CLS");
	system("pause");
	return 0;

}
