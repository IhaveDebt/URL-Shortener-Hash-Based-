#include <iostream>
#include <unordered_map>
#include <string>
using namespace std;

string hashURL(const string& url) {
    unsigned long hash = 5381;
    for (char c : url) hash = ((hash << 5) + hash) + c;
    string key = to_string(hash).substr(0, 6);
    return key;
}

int main() {
    unordered_map<string, string> db;
    string url;
    cout << "Enter URL to shorten: ";
    cin >> url;
    string key = hashURL(url);
    db[key] = url;
    cout << "Shortened URL: https://short.ly/" << key << endl;
    cout << "Original URL: " << db[key] << endl;
}
