# Problem in Multiple Inheritance

### Code

```C++
#include <iostream>

class A{
public:
    void fun() {
        std::cout << "Class A" << std::endl;
    }
};

class B{
public:
    void fun() {
        std::cout << "Class B" << std::endl;
    }
};

// Derived class inherits from B and A
class C : public A, public B {
    
};

int main() {
    C obj;

    obj.fun();

    return 0;
}
```
#### Output
```output
/tmp/KeEYwH8ueM.cpp: In function 'int main()':
/tmp/KeEYwH8ueM.cpp:25:9: error: request for member 'fun' is ambiguous
   25 |     obj.fun();
      |         ^~~
/tmp/KeEYwH8ueM.cpp:13:10: note: candidates are: 'void B::fun()'
   13 |     void fun() {
      |          ^~~
/tmp/KeEYwH8ueM.cpp:6:10: note:                 'void A::fun()'
    6 |     void fun() {
      |          ^~~
```

## Solution 1

### Code
```C++
class C : public A, public B {
public:
    void callAFun() {
        A::fun();
    }

    void callBFun() {
        B::fun();
    }
};
```

## Solution 2

### Code
```C++
class C : public A, public B {
public:
    void fun() {
        A::fun();
    }
};
```
-----

-----

# Diamond Problem in Hybrid Inheritance

### Code
```C++
#include <iostream>

class A {
public:
    void displayA() {
        std::cout << "Class A" << std::endl;
    }
};

class B : public A {
public:
    void displayB() {
        std::cout << "Class B" << std::endl;
    }
};

class C : public A {
public:
    void displayC() {
        std::cout << "Class C" << std::endl;
    }
};

class D : public B, public C {
public:
    void displayD() {
        std::cout << "Class D" << std::endl;
    }
};

int main() {
    D obj;

    obj.displayB();
    obj.displayC();
    obj.displayD();

    // Ambiguity arises here because both B and C inherit from A
    // This causes ambiguity: which displayA() to call?
    obj.displayA();  

    return 0;
}
```

#### Output:

```Output
ERROR!
/tmp/URFRpemY87.cpp: In function 'int main()':
/tmp/URFRpemY87.cpp:45:9: error: request for member 'displayA' is ambiguous
   45 |     obj.displayA();
      |         ^~~~~~~~
/tmp/URFRpemY87.cpp:6:10: note: candidates are: 'void A::displayA()'
    6 |     void displayA() {
      |          ^~~~~~~~
/tmp/URFRpemY87.cpp:6:10: note:                 'void A::displayA()'
```

## Solution - Using Virtual Inheritance

### Code
```C++
#include <iostream>

class A {
public:
    void displayA() {
        std::cout << "Class A" << std::endl;
    }
};

class B : virtual public A {
public:
    void displayB() {
        std::cout << "Class B" << std::endl;
    }
};

class C : virtual public A {
public:
    void displayC() {
        std::cout << "Class C" << std::endl;
    }
};

class D : public B, public C {
public:
    void displayD() {
        std::cout << "Class D" << std::endl;
    }
};

int main() {
    D obj;

    obj.displayB();
    obj.displayC();
    obj.displayD();
    obj.displayA();  // Now works correctly due to virtual inheritance

    return 0;
}
```
