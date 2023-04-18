---
subject: 
category: lab-file
---
>%%Links: [[Lab Files]]%%

# Experiment 5
Feb 7, 2023

## Objective
To write a program to convert regex to context free grammar

---
## Source Code
```plain
#include <iostream>
#include <string>
#include <vector>
#include <cctype>

using namespace std;

void CFG_without_brackets(string str) {
    vector<string> words;
    size_t pos = 0;
    string delimiter = "+";
    while ((pos = str.find(delimiter)) != string::npos) {
        string word = str.substr(0, pos);
        words.push_back(word);
        str.erase(0, pos + delimiter.length());
    }
    words.push_back(str);

    char state1 = 'S';
    char state2 = 'A';

    for (string y : words) {
        for (char x : y) {
            try {
                if (x == '*') {
                    size_t end_index = y.find(x) - 1;
                    if (y[end_index] == ')') {
                        size_t start_index = y.find('(');
                        string temp = y.substr(start_index, end_index - start_index + 1);
                        if (temp != "") {
                            cout << state2 << " -> " << temp << state2 << "|Є" << endl;
                            string temp2 = y.substr(0, start_index) + state2 + y.substr(end_index + 2);
                            y = temp2;
                            state2 = static_cast<char>(state2 + 1);
                        }
                    } else {
                        string temp = y.substr(end_index, 1);
                        size_t start_index = end_index;
                        if (temp != "") {
                            cout << state2 << " -> " << temp << state2 << "|Є" << endl;
                            string temp2 = y.substr(0, start_index) + state2 + y.substr(end_index + 1);
                            y = temp2;
                            state2 = static_cast<char>(state2 + 1);
                        }
                    }
                }
                if (x == '%') {
                    size_t end_index = y.find(x) - 1;
                    if (y[end_index] == ')') {
                        size_t start_index = y.find('(');
                        string temp = y.substr(start_index, end_index - start_index + 1);
                        if (temp != "") {
                            cout << state2 << " -> " << temp << state2 << "|" << temp << endl;
                            string temp2 = y.substr(0, start_index) + state2 + y.substr(end_index + 2);
                            y = temp2;
                            state2 = static_cast<char>(state2 + 1);
                        }
                    } else {
                        string temp = y.substr(end_index, 1);
                        size_t start_index = end_index;
                        if (temp != "") {
                            cout << state2 << " -> " << temp << state2 << "|" << temp << endl;
                            string temp2 = y.substr(0, start_index) + state2 + y.substr(end_index + 1);
                            y = temp2;
                            state2 = static_cast<char>(state2 + 1);
                        }
                    }
                }
            } catch (...) {
                continue;
            }
        }
        string result = "";

    for (char& c : y) {
        if (isalnum(c)) { // check if c is alphanumeric
            result += c;
        }
    }
        cout << "S -> " << result << endl;
    }
}
int main() {
    CFG_without_brackets("a*ca+b*ca");
    return 0;
}
```
---
## Output
```plain
OUTPUT:
A -> aA|Є
S -> Aca
B -> bB|Є
S -> Bca
```