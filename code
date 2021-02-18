# Word_Frequency
Get the word frequency from a text file using I/O streams in c++

#include <iostream>
#include <fstream>
#include <sstream>
#include <string>
#include <cctype>
#include <map>
#include <iomanip>

using namespace std;

void display_prompt();                    //function to display the prompt for getting  filename
void word_frequency(string path);         //function that performs the word count from the input filename
string CleanString(const string phrase);   //function that removes punctuations from words and transforms all word to lowercase
void display_word_frequency(map<string, int> words);     //function that displays the word frequency
typedef void (*FuncCall)();                              //function that allows the passing of one function as parameter to another function
void YorN(FuncCall func);                                 //function that allows the passing of one function as parameter to another function
 
int main()
{
    cout<< "Read document to get Word Frequency\n";
    display_prompt();
    return 0;
}

void display_prompt() {
    string file_name{};
    cout << "\nEnter the file name ..." << endl;
    cin >> file_name;
    size_t pos = file_name.find(".txt");
    if (pos == string::npos)
        file_name += ".txt";
    cout << "\nFile to be read -->" << file_name << endl;
    char choice{};
    cout << "\nDo you want to proceed with reading the file ? (Y/N) .." << endl;
    cin >> choice;
    choice = toupper(choice);
    if (choice == 'Y') {
        cout << "\nReading data from " << file_name << endl;
        word_frequency(file_name);
    }
    else
        cout << "\nExiting the process" << endl;
}

void word_frequency(string path) {
    string file{ path };
    ifstream read_this{};
    string line{};
    string word{};
    read_this.open(file);
    map<string, int> dic;
    if (!read_this) {
        char choice{};
        cout << "\nError reading the file..";
        cout << "\nEnter Y->for displaying the prompt again.\nEnter N ->to quit process." << endl;
        cin >> choice;
        choice = toupper(choice);
        if (choice == 'Y') {
            display_prompt();
            return;
        }
        else {
            cout << "\nProcess terminated..";
            return;
        }
    }
    while (getline(read_this, line)) {
        istringstream ss{ line };
        while (ss >> word) {
            word = CleanString(word);
            dic[word] += 1;
        }
    }
    read_this.close();
    char choice{};
    cout << "\nReading successfull , do you want to see the word frequency?(Y/N)..." << endl;
    cin >> choice;
    choice = toupper(choice);
    if (choice == 'Y')
        display_word_frequency(dic);
    else {
        cout << "\nProcess terminated..";
        return;
    }

}

string CleanString(const string phrase) {
    string word{};
    for (char c : phrase) {
        if (c == '.' || c == '-' || c == ';' || c == ',' || c == '!' || c == ':')
            continue;
        else {
            c = tolower(c);
            word += c;
        }
    }
    return word;
}

void display_word_frequency(map<string, int> words) {
    cout << "\n-----------------The word frequency are listed below---------------\n" << endl;
    cout <<setw(15) << left <<"Word"
        << setw(30) << right << "Frequency" << endl;
    int i = 1;
    for (auto pair : words) {
        cout << i << ")" << setw(15) << left << pair.first
            << setw(50) << left << pair.second << endl;
        i++;
   }
    cout << "\nEnter Y->for displaying the prompt again.\nEnter N ->to quit process." << endl;
    YorN((FuncCall)display_prompt);
}


void YorN( FuncCall func){
    char choice{};
    cin >> choice;
    choice = toupper(choice);
    if (choice == 'Y') {
        func();
        return;
    }
    else {
        cout << "\nProcess terminated..";
        return;
    }
}
