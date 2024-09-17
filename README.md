```c++
#include <iostream>
#include <string>
using namespace std;

string digitToWords(int digit) {
    switch (digit) {
    case 0:
        return "khong";
    case 1:
        return "mot";
    case 2:
        return "hai";
    case 3:
        return "ba";
    case 4:
        return "bon";
    case 5:
        return "nam";
    case 6:
        return "sau";
    case 7:
        return "bay";
    case 8:
        return "tam";
    case 9:
        return "chin";
    default:
        return "";
    }
}

// Trim leading and trailing spaces
string trim(const string &str) {
    size_t first = str.find_first_not_of(' ');
    if (first == string::npos)
        return ""; // No non-space characters
    size_t last = str.find_last_not_of(' ');
    return str.substr(first, (last - first + 1));
}

string readThreeDigitNumber(int number) {
    if (number < 100 || number > 999) {
        return "Invalid number. Please enter a 3-digit number.";
    }

    int hundreds = number / 100;
    int tens = (number / 10) % 10;
    int units = number % 10;

    string result = digitToWords(hundreds) + " tram";

    if (tens == 0 && units != 0) {
        result += " le " + digitToWords(units);
    } else if (tens == 0 && units == 0) {
        // Do nothing, the result already contains "tram"
    } else {
        result += " " + (tens == 1 ? "muoi" : digitToWords(tens) + " muoi");
        if (units != 0) {
            result += " " + (units == 5 ? "lam" : digitToWords(units));
        }
    }

    // Trim any leading or trailing spaces before returning
    return trim(result);
}

int main() {
    int number;
    cin >> number;

    cout << readThreeDigitNumber(number) << endl;

    return 0;
}

```