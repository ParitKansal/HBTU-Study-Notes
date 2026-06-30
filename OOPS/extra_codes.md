### Code 1
```c++
#include <iostream>

class Base {
public:
    void show() {
        std::cout << "Base class show function." << std::endl;
    }
};

class Derived : public Base {
public:
    void show() {
        std::cout << "Derived class show function." << std::endl;
    }
};

int main() {
    Base* ptr1 = new Derived();
    ptr1->show();
    
    Derived* ptr2 = new Derived();
    ptr2->show();
    delete ptr1, ptr2;
    return 0;
}
```
