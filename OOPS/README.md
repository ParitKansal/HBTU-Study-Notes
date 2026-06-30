# Object-Oriented Programming (OOP)

## Table of Contents
- [Core Concepts](#core-concepts)
- [Four Pillars of OOP](#four-pillars-of-oop)
- [Inheritance](#inheritance)
- [Interfaces and Abstract Classes](#interfaces-and-abstract-classes)
- [Constructors and Destructors](#constructors-and-destructors)
- [Virtual Functions](#virtual-functions)
- [Static Members](#static-members)
- [Class vs Struct (C++)](#class-vs-struct-c)
- [OOP vs Structured Programming](#oop-vs-structured-programming)
- [Programming Paradigms](#programming-paradigms)
- [Code Examples](#code-examples)

---

## Core Concepts

**What is OOP?**
Object Oriented Programming is a programming paradigm where software is built from objects that communicate with each other.

**What is a Class?**
A **class** is a user-defined data type that acts as a blueprint — it defines data members and member functions that operate on that data.

**What is an Object?**
An **object** is an instance of a class. It holds its own data and can use the methods defined in the class. Objects are the real-world entities that have a state and behavior.

**What are access specifiers?**
Keywords that control the accessibility of class members. The three main specifiers are:
- `private` — accessible only within the class
- `protected` — accessible within the class and its subclasses
- `public` — accessible from anywhere

**How much memory does a class occupy?**
A class definition itself occupies minimal memory. Instance variables get memory only when an object is created — each object has its own copy. Methods are shared across all instances.

**Is it always necessary to create objects from a class?**
No. `static` methods and variables can be accessed directly via the class name without creating an object. Non-static members require an object.

---

## Four Pillars of OOP

### Encapsulation
Binding data and the methods that manipulate it into a single unit, hiding sensitive data from the outside world.

### Abstraction
Showing only the necessary details and hiding irrelevant implementation from the user. Implemented using classes and interfaces.

### Polymorphism
The ability of code to behave differently for different contexts.

| Type | Also Called | When Resolved |
| :--- | :--- | :--- |
| Compile-time polymorphism | Static / Early binding | At compile time |
| Runtime polymorphism | Dynamic / Late binding | At runtime |

**Compile-time:** Achieved through method overloading and operator overloading.  
**Runtime:** Achieved through method overriding with virtual functions.

![Polymorphism](https://raw.githubusercontent.com/ParitKansal/photos/main/polymorphism.png)

**Overloading vs Overriding**

| | Overloading | Overriding |
| :--- | :--- | :--- |
| Method name | Same | Same |
| Parameters | Different | Same |
| Scope | Same class | Superclass and subclass |
| Resolved at | Compile time | Runtime |

**Operator Overloading:** Giving additional meanings to standard operators when applied to user-defined types.

### Inheritance
A class (child) is derived from another class (parent) and reuses its data and implementation.

**Advantages of OOP**
1. Enhanced code reusability
2. Easier to maintain and update
3. Better data security through encapsulation

**Disadvantages of OOP**
1. Requires proper planning; can be tricky to design well
2. Not suitable for all types of problems
3. Programs are often longer than procedural equivalents for simple tasks

---

## Inheritance

**Limitations of Inheritance**
- Takes longer to process as it must pass through several classes
- Changes may need to be made in both base and child class simultaneously
- Incorrect implementation can lead to bugs and unexpected output

**Types of Inheritance**

| Inheritance Type | Java | Python | C++ |
| :--- | :--- | :--- | :--- |
| Single | Yes | Yes | Yes |
| Multilevel | Yes | Yes | Yes |
| Hierarchical | Yes | Yes | Yes |
| Multiple | Via interfaces only | Yes | Yes |
| Hybrid | Via interfaces only | Yes | Yes |
| Virtual | N/A | N/A | Yes (`virtual` keyword) |

**C++:** Ambiguity errors occur when multiple base classes define a function with the same name (see [Multiple Inheritance Problem](#problem-in-multiple-inheritance)).

**Python:** Supports multiple inheritance directly. Ambiguity is resolved using **C3 linearization (MRO — Method Resolution Order)**, which works similarly to BFS.

---

## Interfaces and Abstract Classes

**What is an Interface?**
An interface defines method signatures without implementations. It is a contract that implementing classes must fulfill. You cannot instantiate an interface directly.

**Abstract Class vs Interface**

| Feature | Abstract Class | Interface |
| :--- | :--- | :--- |
| Methods | Can have both abstract and concrete methods | Only abstract (pure virtual) methods |
| Variables | Can have any kind of member variables | Only `static` and `final` (constants) |
| Multiple inheritance | Limited (complex in C++) | Supported — a class can implement many |

---

## Constructors and Destructors

**What is a Constructor?**
A constructor is a special block of code that runs when an object is created. It has the same name as the class and has no return type.

**Types of Constructors (C++)**

| Type | Description |
| :--- | :--- |
| Default | No arguments; auto-generated by compiler if none is defined |
| Non-parameterized | User-defined, no arguments |
| Parameterized | Takes arguments to initialize with specific values |
| Copy | Initializes a new object as a copy of an existing one |

**Copy Constructor Example (C++)**
```cpp
class Base {
    int a, b;
    Base(Base& obj) {
        a = obj.a;
        b = obj.b;
    }
};
```

**Can constructors be overloaded?** Yes — define multiple constructors with different parameter lists.

**What is a Destructor?**
A destructor is called automatically when an object goes out of scope or is deleted.

| Language | Destructor |
| :--- | :--- |
| C++ | `~ClassName()` |
| Python | `__del__` |
| Java | No destructor; GC handles cleanup (`finalize()` was deprecated in Java 9) |

**Can destructors be overloaded?** No — a class can have only one destructor.

---

## Virtual Functions

**Virtual Function vs Pure Virtual Function**

| Feature | Virtual Function | Pure Virtual Function |
| :--- | :--- | :--- |
| Purpose | Override parent method; provides default behavior | Forces derived class to provide an implementation |
| Declaration | `virtual void func() {}` | `virtual void func() = 0;` |
| Base class implementation | Allowed | Not allowed |
| Can instantiate base class | Yes | No (class becomes abstract) |

---

## Static Members

Static members belong to the class, not to any individual object. They are shared across all instances.

```cpp
#include <iostream>

class MyClass {
public:
    static int classVar;

    MyClass() {
        classVar++;
    }

    static void displayClassVar() {
        std::cout << "Class Variable: " << classVar << std::endl;
    }
};

int MyClass::classVar = 0;

int main() {
    MyClass obj1;
    MyClass obj2;
    MyClass::displayClassVar(); // Output: Class Variable: 2
    return 0;
}
```

---

## Class vs Struct (C++)

| Feature | Class | Struct |
| :--- | :--- | :--- |
| Default access specifier | `private` | `public` |
| Default inheritance | `private` | `public` |
| Common usage | Full OOP with encapsulation | Plain data grouping |
| Constructors/Destructors | Yes | Yes |
| Virtual functions | Yes | Yes |

---

## OOP vs Structured Programming

| OOP | Structured Programming |
| :--- | :--- |
| Bottom-up design — build objects, then compose them | Top-down design — break problem into steps |
| Data encapsulated inside objects | Data flows freely across the program |
| Reuse via inheritance and polymorphism | Reuse via functions and loops |
| Methods dispatched dynamically at runtime | Functions called sequentially |
| Easier to extend and modify | Changes can ripple across many procedures |

---

## Programming Paradigms

### 1. Imperative Programming
Focuses on **how** to do things — a sequence of statements that change program state.

- **1.1 Procedural** — structured as a series of procedures/functions. Examples: C, Pascal, Fortran
- **1.2 Object-Oriented** — structured around objects with state and behavior. Examples: Java, C++, Python
- **1.3 Parallel** — tasks split to run simultaneously. Examples: C (OpenMP/MPI), Go, Erlang

### 2. Declarative Programming
Focuses on **what** to do — describes the desired outcome without specifying control flow.

- **2.1 Logical** — based on formal logic and facts/rules. Examples: Prolog, Mercury
- **2.2 Functional** — programs built by composing pure functions. Examples: Haskell, Lisp, Scala
- **2.3 Database** — manipulating structured data. Examples: SQL, PL/SQL

---

## Code Examples

### Abstract Class with Non-final Member Variable

Demonstrates the four ways to access and modify a protected member variable in an abstract class hierarchy.

```cpp
#include <iostream>

class AbstractClass {
protected:
    double a;

public:
    AbstractClass(double w) : a(w) {}

    virtual double fun1() const = 0;
    virtual double fun2() = 0;

    void seta(double w) { a = w; }
    double geta() const { return a; }

    virtual ~AbstractClass() {}
};

class ClassA : public AbstractClass {
public:
    ClassA(double r) : AbstractClass(r) {}

    // const function: cannot modify a, can only call other const functions
    double fun1() const override {
        return geta();
    }

    // non-const function: can modify a directly
    double fun2() override {
        a = 6;
        return geta();
    }

    double fun3() {
        a = 7;
        return a;
    }
};

int main() {
    AbstractClass* obj1 = new ClassA(5.0);
    std::cout << obj1->fun1() << " " << obj1->fun2() << std::endl; // 5 6

    ClassA* obj2 = new ClassA(5.0);
    std::cout << obj2->fun1() << " " << obj2->fun2() << " " << obj2->fun3() << std::endl; // 5 6 7

    delete obj1;
    delete obj2;
    return 0;
}
```

---

### Interface Example (IShape)

Demonstrates how a C++ interface (pure virtual class) enforces a contract on derived classes.

```cpp
#include <iostream>
#include <cmath>

class IShape {
public:
    virtual double area() const = 0;
    virtual double perimeter() const = 0;
    virtual ~IShape() {}
};

class Circle : public IShape {
    double radius;
public:
    Circle(double r) : radius(r) {}
    double area() const override { return M_PI * radius * radius; }
    double perimeter() const override { return 2 * M_PI * radius; }
};

class Rectangle : public IShape {
    double width, height;
public:
    Rectangle(double w, double h) : width(w), height(h) {}
    double area() const override { return width * height; }
    double perimeter() const override { return 2 * (width + height); }
};

int main() {
    IShape* circle = new Circle(5.0);
    IShape* rectangle = new Rectangle(4.0, 6.0);

    std::cout << "Circle Area: " << circle->area() << std::endl;
    std::cout << "Circle Perimeter: " << circle->perimeter() << std::endl;
    std::cout << "Rectangle Area: " << rectangle->area() << std::endl;
    std::cout << "Rectangle Perimeter: " << rectangle->perimeter() << std::endl;

    delete circle;
    delete rectangle;
    return 0;
}
```

---

### Problem in Multiple Inheritance

When two base classes define a method with the same name, calling it from the derived class is ambiguous.

```cpp
#include <iostream>

class A {
public:
    void fun() { std::cout << "Class A" << std::endl; }
};

class B {
public:
    void fun() { std::cout << "Class B" << std::endl; }
};

class C : public A, public B {};

int main() {
    C obj;
    obj.fun(); // ERROR: ambiguous
    return 0;
}
```

**Error:**
```
error: request for member 'fun' is ambiguous
```

**Solution 1 — Explicit scope resolution:**
```cpp
class C : public A, public B {
public:
    void callAFun() { A::fun(); }
    void callBFun() { B::fun(); }
};
```

**Solution 2 — Override and delegate:**
```cpp
class C : public A, public B {
public:
    void fun() { A::fun(); }
};
```

---

### Diamond Problem in Hybrid Inheritance

When D inherits from both B and C, and both inherit from A, there are two copies of A inside D — causing ambiguity.

```cpp
#include <iostream>

class A {
public:
    void displayA() { std::cout << "Class A" << std::endl; }
};

class B : public A {
public:
    void displayB() { std::cout << "Class B" << std::endl; }
};

class C : public A {
public:
    void displayC() { std::cout << "Class C" << std::endl; }
};

class D : public B, public C {
public:
    void displayD() { std::cout << "Class D" << std::endl; }
};

int main() {
    D obj;
    obj.displayA(); // ERROR: ambiguous — two copies of A exist in D
    return 0;
}
```

**Solution — Virtual Inheritance** (ensures only one shared copy of A):

```cpp
class B : virtual public A { ... };
class C : virtual public A { ... };
class D : public B, public C { ... }; // Now only one A

// obj.displayA(); works correctly
```

---

### Method Hiding vs Runtime Polymorphism

Without `virtual`, the method called depends on the **pointer type**, not the object type (method hiding). With `virtual`, it depends on the **actual object** (runtime polymorphism).

```cpp
#include <iostream>

class Base {
public:
    void show() {  // Non-virtual: resolved at compile time by pointer type
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
    ptr1->show();    // Calls Base::show() — method hiding, not polymorphism

    Derived* ptr2 = new Derived();
    ptr2->show();    // Calls Derived::show()

    delete ptr1;
    delete ptr2;
    return 0;
}
```

**Output:**
```
Base class show function.
Derived class show function.
```

> To get runtime polymorphism, declare `show()` as `virtual` in `Base`.
