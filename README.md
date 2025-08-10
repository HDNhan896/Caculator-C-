#include <iostream>
#include <iomanip>
#define ll long long

using namespace std;

struct History {
    double a;
    char caculation;
    double b;
    double total;
};
void initHistory(History H[]){
    for (int i = 0 ; i < 10000 ; i ++){
        H[i].a = 0;
        H[i].b = 0;
        H[i].caculation = NULL;
    }
}
void printHistory(History H[], int size){
    for (int i = 0 ; i < size ; i ++){
        cout << H[i].a << " " << H[i].caculation << " " << H[i].b << " = " << H[i].total << endl;
    }
}

void addition(double& result, int i, History H[]){
    --i;
    H[i].a = result;
    result += H[i].b;
    H[i].caculation = '+';
    H[i].total = H[i].a + H[i].b;
}
void subtraction(double& result, int i, History H[]){
    --i;
    H[i].a = result;
    result -= H[i].b;
    H[i].caculation = '-';
    H[i].total = H[i].a - H[i].b;
}
void multiplication(double& result, int i, History H[]){
    --i;
    H[i].a = result;
    result *= H[i].b;
    H[i].caculation = 'x';
    H[i].total = H[i].a * H[i].b;
}
void division(double& result, int i, History H[]){
    --i;
    H[i].a = result;
    result /= H[i].b;
    H[i].caculation = '/';
    H[i].total = H[i].a / H[i].b;
}

int main(){
    History H[10000]; initHistory(H);
    double result = 0, a = 0;
    char choice = NULL, i = 0;
    cin >> a;
    result = a;
    while (choice != '='){
        switch (choice){
            case '+':
                addition(result, i, H);
                break;
            case '-':
                subtraction(result, i, H);
                break;
            case 'x':
                multiplication(result, i, H);
                break;
            case '/':
                division(result, i, H);
                break;
        } 
        cout << "result: " << result << endl;
        cin >> choice;
        if (choice == '='){
            printHistory(H, i);
        } cin >> a; H[i].b = a;
        i++;
    } return 0;
}

