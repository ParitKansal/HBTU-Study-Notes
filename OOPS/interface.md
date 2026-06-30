```bash
#include <iostream>
#include <cmath>

// Interface: IShape
class IShape {
public:
    // Pure virtual function to compute the area
    virtual double area() const = 0;

    // Pure virtual function to compute the perimeter
    virtual double perimeter() const = 0;

    // Virtual destructor
    virtual ~IShape() {}
};

// Implementing the IShape interface for Circle
class Circle : public IShape {
private:
    double radius;
public:
    Circle(double r) : radius(r) {}

    // Implementing area() method
    double area() const override {
        return M_PI * radius * radius;
    }

    // Implementing perimeter() method
    double perimeter() const override {
        return 2 * M_PI * radius;
    }
};

// Implementing the IShape interface for Rectangle
class Rectangle : public IShape {
private:
    double width, height;
public:
    Rectangle(double w, double h) : width(w), height(h) {}

    // Implementing area() method
    double area() const override {
        return width * height;
    }

    // Implementing perimeter() method
    double perimeter() const override {
        return 2 * (width + height);
    }
};

// Main function demonstrating the use of the interface
int main() {
    // Creating objects for Circle and Rectangle
    IShape* circle = new Circle(5.0);     // Circle with radius 5.0
    IShape* rectangle = new Rectangle(4.0, 6.0); // Rectangle with width 4.0 and height 6.0

    // Output Circle details
    std::cout << "Circle Area: " << circle->area() << std::endl;
    std::cout << "Circle Perimeter: " << circle->perimeter() << std::endl;

    // Output Rectangle details
    std::cout << "Rectangle Area: " << rectangle->area() << std::endl;
    std::cout << "Rectangle Perimeter: " << rectangle->perimeter() << std::endl;

    // Clean up dynamically allocated memory
    delete circle;
    delete rectangle;

    return 0;
}
```