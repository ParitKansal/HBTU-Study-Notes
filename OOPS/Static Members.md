```bash
#include <iostream>

class MyClass {
public:
    static int classVar; // Class-level attribute

    MyClass() {
        // Constructor
        classVar++; // Increment class variable when a new object is created
    }

    static void displayClassVar() {
        std::cout << "Class Variable: " << classVar << std::endl;
    }
};

// Define the static member outside the class
int MyClass::classVar = 0;

int main() {
    MyClass obj1; // First object
    MyClass obj2; // Second object

    MyClass::displayClassVar(); // Displays 2, since two objects were created
    
    return 0;
}


```