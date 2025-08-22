#include <iostream>
#include <string>
#include <csdlib>
#include <ctime>
using namespace std;

string decimalToBinary(int decimal) { // Decimal to Binary
    string binary = "";
    if (decimal == 0) return "0";
    while (decimal > 0) {
        binary = to_string(decimal % 2) + binary;
        decimal /= 2;
    }
    return binary;
}

int binaryToDecimal(string binary) { // Binary to Decimal
    int decimal = 0;
    for (char bit : binary) {
        if (bit != '0' && bit != '1') {
            cout << "Invalid binary input.\n";
            return -1;
        }
        decimal = decimal * 2 + (bit - '0');
    }
    return decimal;
}

string decimalToHexadecimal(int decimal) { // Decimal to Hexadecimal
    string hex = "";
    char hexDigits[] = "0123456789ABCDEF";
    if (decimal == 0) return "0";
    while (decimal > 0) {
        int remainder = decimal % 16;
        hex = hexDigits[remainder] + hex;
        decimal /= 16;
    }
    return hex;
}

int hexadecimalToDecimal(string hex) { // Hexadecimal to Decimal
    int decimal = 0;
    for (char ch : hex) {
        decimal *= 16;
        if (ch >= '0' && ch <= '9') {
            decimal += ch - '0';
        } else if (ch >= 'A' && ch <= 'F') {
            decimal += ch - 'A' + 10;
        } else {
            cout << "Invalid hexadecimal input.\n";
            return -1;
        }
    }
    return decimal;
}

int main() {
    int choice;
    cout << "1. Decimal to Binary\n";
    cout << "2. Binary to Decimal\n";
    cout << "3. Decimal to Hexadecimal\n";
    cout << "4. Hexadecimal to Decimal\n";
    cout << "Choose an option (1-4): ";
    cin >> choice;

    if (choice == 1) {
        int decimal;
        cout << "Enter a decimal number: ";
        cin >> decimal;
        cout << "Binary: " << decimalToBinary(decimal) << endl;
    } else if (choice == 2) {
        string binary;
        cout << "Enter a binary number: ";
        cin >> binary;
        cout << "Decimal: " << binaryToDecimal(binary) << endl;
    } else if (choice == 3) {
        int decimal;
        cout << "Enter a decimal number: ";
        cin >> decimal;
        cout << "Hexadecimal: " << decimalToHexadecimal(decimal) << endl;
    } else if (choice == 4) {
        string hex;
        cout << "Enter a hexadecimal number: ";
        cin >> hex;
        cout << "Decimal: " << hexadecimalToDecimal(hex) << endl;
    } else {
        cout << "Invalid choice.\n";
    }

    return 0;
}

