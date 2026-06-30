```bash
#include <iostream>

class AbstractClass {
protected:
    double a;  // Non-final member variable

public:
    AbstractClass(double w) : a(w) {}

    virtual double fun1() const = 0;
    virtual double fun2() = 0;

    // Method 1: Modifying the non-final variable
    void seta(double w) {
        a = w;
    }

    // Getter for non-final variable, marked as const
    double geta() const {
        return a;
    }

    virtual ~AbstractClass() {}
};

class ClassA : public AbstractClass {
public:
    // // Method 2: Use contructors Constructor
    ClassA(double r) : AbstractClass(r) {}

    // Do not allow changing the value of non-final variables in a const function and only can call const functions only 
    double fun1() const override {
        return geta();
    }

    // Method 3: Allows changing the value of non-final variables
    double fun2() override {
        a = 6;  // Modifying the non-final variable
        return geta();
    }

    // Method 4: Another function that changes the value of a non-final variable
    double fun3() {
        a = 7;
        return a;
    }
};

int main() {
    AbstractClass* obj1 = new ClassA(5.0);
    std::cout << obj1->fun1() << " " << obj1->fun2() << std::endl;

    ClassA* obj2 = new ClassA(5.0);
    std::cout << obj2->fun1() << " " << obj2->fun2() << " " << obj2->fun3() << std::endl;

    // Clean up
    delete obj1;
    delete obj2;

    return 0;
}

```