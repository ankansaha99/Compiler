#include <iostream>
#include <fstream>
#include <string>

using namespace std;

int main() {
    ifstream infile("As.txt");

   if (!infile) {
         cout << "File missing!" << endl;
        return 0;
    }

string text;

    while (getline(infile, text)) {
        string word = "";

        for (int i = 0; i < text.length(); i++) {
            char ch = text[i];

            if ((ch >= 'a' && ch <= 'z') ||
                (ch >= 'A' && ch <= 'Z') ||
                (ch >= '0' && ch <= '9') ||
                ch == '_') {

                word += ch;
            }
   else {
    if (word != "") {
        if (word == "int" || word == "return") {
         cout << "Keyword is: " << word << endl;
         }
            else if (word[0] >= '0' && word[0] <= '9') {
                cout << "Number is: " << word << endl;
                }
         else {
                cout << "Identifier is: " << word << endl;
                }
                    word = "";
                }


            if (ch == ' ') continue;

            if (ch == '"') {
                    string str = "\"";
                    i++;
                    while (i < text.length() && text[i] != '"') {
                        str += text[i];
                        i++;
                    }
                    str += "\"";
                    cout << "String is: " << str << endl;
                }
                else {

                    if (ch == '=' || ch == '<' || ch == '>') {
                        cout << "Operator is: " << ch << endl;
                    }
                    else {
                        cout << "Symbol is: " << ch << endl;
                    }
                }
            }
        }


        if (word != "") {
            if (word == "int" || word == "return") {
                cout << "Keyword is: " << word << endl;
            }
            else if (word[0] >= '0' && word[0] <= '9') {
                cout << "Number is: " << word << endl;
            }
            else {
                cout << "Identifier is: " << word << endl;
            }
        }
    }

    infile.close();
    return 0;
}
