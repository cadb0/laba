#include <iostream>
#include <climits>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");

    unsigned int number;
    cout << "Введите число: \n";
    cin >> number;
    number = number & 0xFFFFFF;
    cout << "Число с обнуленными старшими байтами: " << number << endl << '\n';

    cout << "int: " << sizeof(int) << " bytes" << endl;
    cout << "short int: " << sizeof(short int) << " bytes" << endl;
    cout << "long int: " << sizeof(long int) << " bytes" << endl;
    cout << "float: " << sizeof(float) << " bytes" << endl;
    cout << "double: " << sizeof(double) << " bytes" << endl;
    cout << "long double: " << sizeof(long double) << " bytes" << endl;
    cout << "char: " << sizeof(char) << " bytes" << endl;
    cout << "bool: " << sizeof(bool) << " bytes" << endl << '\n';


    union {
        uint32_t Ivalue;
        float Fvalue;
    } float_union;

    cout << "Введите число (float): ";
    cin >> float_union.Fvalue;

    cout << "В двоичном виде (float):\n";
    for (int i = 31; i >= 0; i--) {
        if (float_union.Ivalue & (1u << i)) {
            cout << "1";
        }
        else {
            cout << "0";
        }
        if (i == 31 || i == 23) cout << " ";
    }
    cout << endl << endl;


    union {
        uint64_t Ivalue;
        double Dvalue;
    } double_union;

    cout << "Введите число (double): ";
    cin >> double_union.Dvalue;

    cout << "В двоичном виде (double):\n";
    for (int i = 63; i >= 0; i--) {
        if (double_union.Ivalue & (1ULL << i)) {
            cout << "1";
        }
        else {
            cout << "0";
        }
        if (i == 63 || i == 52) cout << " ";
    }
    cout << endl;

    return 0;
}
