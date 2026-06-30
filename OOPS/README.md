# **OOPS**
______
**What is Object Oriented Programming (OOPs)?**

O*bject* O*riented* P*rogramming* (also known as OOPs) is a programming paradigm where the complete software is formed by objects which talk with each other.

**What is a Class?**

A **class** is a building block of Object-Oriented Programs. It is a user-defined data type that contains the data members and member functions that operate on the data members. It is like a blueprint or template of objects having common properties and methods.

**What is an Object?**

An **object** is an instance of a class. An object is a collection of data and the methods which operate on that data. Data members and methods of a class cannot be used directly. We need to create an object (or instance) of the class to use them. In simple terms, they are the actual world entities that have a state and behavior.

**What are the main features of OOPs?**

1. Encapsulation  
2. Data Abstraction  
3. Polymorphism  
4. Inheritance

**What is Encapsulation?**

Encapsulation is the binding of data and methods that manipulate them into a single unit such that the sensitive data is hidden from the users.

**What is Abstraction?**

Abstraction means showing only the necessary information and hiding the other irrelevant information from the user. Abstraction is implemented using classes and interfaces.

**What is Polymorphism?**

Polymorphism means some code to behave differently for different contexts.

**A) Compile-Time Polymorphism / Static polymorphism / Early binding**

The type of polymorphism where the binding of the call to its code is done at the compile time.

**B) Runtime Polymorphism** **/ Dynamic polymorphism / Late binding**

The type of polymorphism where the binding of the call to its code is done at the compile time runtime or execution.

![](https://github.com/ParitKansal/photos/blob/main/polymorphims.png)

**What is Inheritance? What is its purpose?**

The idea of inheritance is simple, a class is derived from another class and uses data and implementation of that other class.

**What are access specifiers? What is their significance in OOPs?**

Access specifiers are special types of keywords that are used to specify or control the accessibility of entities like classes, methods, and so on. **Private**, **Public**, and **Protected** are examples of access specifiers or access modifiers.

**Advantages of OOP**

1. OOP provides enhanced code reusability.  
2. The code is easier to maintain and update.  
3. It provides better data security.

**Disadvantages of OOP**

1. Proper planning is required because OOP can be a bit tricky.  
2. The OOP concept is not suitable for all kinds of problems.  
3. The length of the programs is much larger in comparison to the procedural approach, especially in cases of short programs.

**What other paradigms of programming exist besides OOPs?**

**1\. Imperative Programming Paradigm**

Imperative programming is about how to do things. It focuses on changing the program's state through specific instructions, telling the computer exactly what steps to follow to achieve a goal.

**Key Features:**

* **State Changes:** Programs are composed of a series of statements that change the program's state.  
* **Control Flow:** It involves sequences of commands (like loops and conditionals) to control the flow of execution.  
  **1.1**  **Procedural Programming**: Procedural programming is based on the concept of procedures (or functions). It structures the program as a series of steps or procedures to follow. **Examples**: C, Pascal, Fortran, BASIC

**1.2 Object-Oriented Programming (OOP):** OOP treats everything as an object that has properties (state) and methods (behavior). It organizes the program around these objects. **Examples: Java, C++, Python, Ruby**

**1.3 Parallel Programming:** Parallel programming involves breaking down tasks into smaller parts that can be executed simultaneously, improving efficiency and performance. **Examples: C (with OpenMP or MPI), Java (with concurrency libraries), Go, Erlang**

**2\. Declarative Programming Paradigm**

Declarative programming focuses on what to do rather than how to do it. You specify the desired outcome without explicitly detailing the steps to achieve it.

**Key Features:**

* **Logic Over Control Flow:** It expresses the logic of a computation without considering the control flow.  
* **Higher-Level Abstraction:** It allows for a higher level of abstraction than imperative programming.

**2.1 Logical Programming:** Logical programming is based on formal logic. You define facts and rules that express the relationships between data. **Examples**: Prolog, Mercury

**2.2 Functional Programming:** Functional programming creates programs by applying and composing functions. It emphasizes the use of pure functions without side effects. **Examples: Haskell, Lisp, Scala, F\#**

**2.3 Database Programming:** Database programming involves managing and manipulating data stored in databases. It utilizes specific programming models to interact with structured data. **Examples**: SQL, PL/SQL, T-SQL

**What is the difference between Structured Programming and Object Oriented Programming?**

| Object-Oriented Programming (OOP) | Structured Programming |
| :---- | :---- |
| OOP is based on objects that have state (attributes) and behavior (methods). | Structured programming focuses on the logical structure of a program, dividing it into functions and modules. |
| It follows a **bottom-up** approach, starting with defining objects and their interactions. | It follows a **top-down** approach, starting with a high-level overview and breaking it down into smaller parts. |
| Data flow is restricted to authorized parts of the program, enhancing data security. | There are no restrictions on data flow; any part of the program can access data freely. |
| Code reusability is achieved through inheritance and polymorphism, allowing the creation of new classes from existing ones. | Code reusability is achieved using functions and loops, but it's limited compared to OOP. |
| Methods can be dynamically called based on object behavior and runtime needs. | Functions are called sequentially, processing code step by step. |
| Modifying and updating code is generally easier due to encapsulation and abstraction. | Modifying code can be more challenging since changes may affect multiple parts of the program. |
| Emphasizes data as a core component, encapsulating it within objects. | Emphasizes the code logic and flow, often prioritizing procedures over data. |

 

**What is the difference between overloading and overriding?**

**Overloading:** Same method name, different parameter lists, occurs within the same class, resolved at compile time.

**Overriding:** Same method name and parameters, occurs between superclass and subclass, resolved at runtime.

**Operator Overloading:** Refers to giving additional meanings to standard operators when applied to user-defined types.

**Are there any limitations on Inheritance?**

* As it must pass through several classes to be implemented, inheritance takes longer to process.  
* If changes need to be made, they may need to be made in both base class and child class at the same time.  
* If inheritance is not implemented correctly, this could result in unforeseen mistakes or inaccurate outputs.

**What different types of Inheritance are there?**

| Inheritance Type | Java | Python | C++ |
| :---- | :---- | :---- | :---- |
| **Single Inheritance** | Yes | Yes | Yes |
| **Multilevel Inheritance** | Yes | Yes | Yes |
| **Hierarchical Inheritance** | Yes | Yes | Yes |
| **Multiple Inheritance** | Via interfaces | Yes | Yes |
| **Hybrid Inheritance** | Via interfaces | Yes | Yes |
| **Virtual Inheritance** | N/A | N/A | Yes (with virtual) |

**C++:** Error may occur when it inherits many different functions of same declaration from different classes.

**Python**: Supports multiple inheritance directly for classes, and method resolution is handled using the C3 linearization (MRO \- Method Resolution Order) which work like BFS. This resolving errors.

Link: [https://github.com/ParitKansal/OOPS/blob/main/Inheritance.md](https://github.com/ParitKansal/OOPS/blob/main/Inheritance.md)

**What is an interface?**

A unique class type known as an interface contains methods but not their definitions. Inside an interface, only method declaration is permitted. You cannot make objects using an interface.

Link \- [https://github.com/ParitKansal/OOPS/blob/main/interface.md](https://github.com/ParitKansal/OOPS/blob/main/interface.md)

**How is an abstract class different from an interface?**

| Abstract Class | Interface |
| :---- | :---- |
| Can have both abstract (pure virtual) and non-abstract (concrete) methods. | Can only have abstract (pure virtual) methods. |
| Can have final (constant), non-final, static, and non-static member variables. | Can only have static and final (constants) variables. |
| Does not support multiple inheritance in the same way as interfaces (C++ allows multiple inheritance, but with some complexities). | Supports multiple inheritance, allowing a class to implement multiple interfaces. |

 

**How much memory does a class occupy?**

A class itself occupies memory for its definition and any class-level attributes, but it doesn't allocate memory for instance variables until an object is created. Each instance of a class has its own memory for instance variables, while methods are shared among instances.

**Is it always necessary to create objects from class?**

**Creating Objects:** You must create objects to access non-static methods and variables.

**No Objects Needed:** You do not need to create objects to access static methods or variables; you can call them directly using the class name.

**What is the difference between a structure and a class in C++?**

| Feature | Class | Struct |
| :---- | :---- | :---- |
| **Default Access Specifier** | Private | Public |
| **Inheritance** | Default is private | Default is public |
| **Member Functions** | Can have member functions and can be abstract. | Can have member functions and can be abstract, but usually does not. |
| **Constructor/Destructor** | Can define constructors and destructors. | Can define constructors and destructors. |
| **Polymorphism / Virtual Function** | Supports polymorphism with virtual functions. | Supports polymorphism with virtual functions. |

 

**What is Constructor?**

A constructor is a block of code that initializes the newly created object. A constructor resembles an instance method but it’s not a method as it doesn’t have a return type. It generally is the method having the same name as the class but in some languages, it might differ like in python, a constructor is named **\_\_init\_\_.** 

**What are the various types of constructors in C++?**

The most common classification of constructors includes:

1. **Default Constructor**  
2. **Non-Parameterized Constructor**  
3. **Parameterized Constructor**  
4. **Copy Constructor**

**1\. Default Constructor**

The default constructor is a constructor that doesn’t take any arguments. It is a non-parameterized constructor that is automatically defined by the compiler when no explicit constructor definition is provided.

**2\. Non-Parameterized Constructor**

It is a user-defined constructor having no arguments or parameters.

**3\. Parameterized Constructor**

The constructors that take some arguments are known as parameterized constructors.

**4\. Copy Constructor**

A copy constructor is a member function that initializes an object using another object of the same class.

**Example:**

```C++  
class base {  
    int a, b;  
    base(base& obj)  
    {  
        a = obj.a;  
        b = obj.b;  
    }  
}
```

**What is a destructor?**

A destructor is a method that is automatically called when the object is made of scope or destroyed.

In C++, the destructor name is also the same as the class name but with the (**\~**) **tilde symbol** as the prefix.

In Python, the destructor is named **\_\_del\_\_**.

In Java, the garbage collector automatically deletes the useless objects so there is no concept of destructor in Java. We could have used finalize() method as a workaround for the java destructor but it is also deprecated since Java 9\.

**Can we overload the constructor in a class?**

Yes, constructor overloading is done when we want to define multiple constructors with different parameters (number and type).

**Can we overload the destructor in a class?**

No, a destructor cannot be overloaded in a class. There can only be one destructor present in a class.

**Difference b/w Virtual Functions and Pure Virtual Functions**

| Feature | Virtual Functions | Pure Virtual Functions |
| :---- | :---- | :---- |
| **Definition** | A virtual function is a function that is used to override a method of the parent class in the derived class. | A pure virtual function, also known as an abstract function is a member function that doesn’t contain any statements.  |
| **Declaration** | Declared with the virtual keyword. | Declared with \= 0 to signify it is a pure virtual function. |
| **Implementation** | Can have an implementation in the base class, providing default behavior. | Must not have an implementation in the base class, enforcing derived classes to provide one. |
| **Instantiation** | Can instantiate the base class, allowing creation of base class objects. | Cannot instantiate the base class (it becomes abstract), ensuring that only derived classes can be instantiated. |
| **Example** | virtual double function () {return 0;} | virtual double function () const \= 0; |
