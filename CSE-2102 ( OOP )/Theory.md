# 🧩 1️⃣ What is OOP (Bottom-Up Approach)

OOP (Object-Oriented Programming) builds programs using objects and classes.
It’s called a Bottom-Up approach because:

You start from small building blocks (objects)

Combine them to form larger systems (the whole program)

Example:
```cpp
class Student {
public:
    string name;
    int id;
};
int main() {
    Student s1;  // object created (bottom element)
}
```
# ⚙️ 2️⃣ Procedural & Top-Down Approach

Procedural Programming: Program is divided into functions.

Top-Down: Start from the main problem → break it into smaller sub-problems → solve each with functions.

Example (C style):
```cpp
void input();
void process();
void output();
int main() {
    input();
    process();
    output();
}
```

OOP is the opposite → Bottom-Up (create reusable objects first).

# 🏗️ 3️⃣ Class and Object — Why Class is a Blueprint

Class: A template or design for creating objects.

Object: A real instance of a class.

Why called  Class is a Blueprint?
Because a class only describes how an object should look and behave — like a design of a house.

Example:
```cpp
class Car {
public:
    string model;
    int year;
    void show() {
        cout << model << " " << year << endl;
    }
};
int main() {
    Car c1;
    c1.model = "Toyota";
    c1.year = 2020;
    c1.show();
}
```
# 🌐 4️⃣ Defining Function Outside Class

You can declare a function inside the class and define it outside using the scope resolution operator (::).

Example:
```cpp
class Student {
public:
    void show();
};
void Student::show() {
    cout << "Hello Student";
}
```
# 🧱 5️⃣ Constructor

A special function that automatically runs when an object is created.

Rules:

Same name as the class

No return type

Used to initialize data

Example:
```cpp
class A {
public:
    A() { cout << "Constructor called"; }
};
```
🧹 6️⃣ Destructor

Opposite of constructor — runs automatically when an object is destroyed.

Syntax:
```cpp
~ClassName() { ... }
```

Example:
```cpp
class A {
public:
    ~A() { cout << "Object destroyed"; }
};
```
# ⚒️ 7️⃣ Constructor Overloading

Multiple constructors in the same class but with different parameters.

Example:
```cpp
class Box {
public:
    Box() { cout << "Default constructor\n"; }
    Box(int w, int h) { cout << "Box: " << w << "x" << h << endl; }
};
```
# ⚖️ 8️⃣ Data Function vs Constructor
| Feature | Data Function | Constructor       |
| ------- | ------------- | ----------------- |
| Call    | Manual        | Auto              |
| Name    | Any           | Same as class     |
| Return  | Can have      | No return         |
| Purpose | Perform tasks | Initialize object |

🔐 9️⃣ Friend Class & Friend Function

A friend function can access private and protected members of a class.

Declared with keyword friend.

Example:
```cpp
class Box {
private:
    int width;
public:
    Box() { width = 10; }
    friend void show(Box);
};
void show(Box b) {
    cout << "Width = " << b.width;
}
```
# 🧬 🔟 Inheritance & Classification

Inheritance allows a class (child) to use the properties and functions of another class (parent).

Types of Inheritance:

Single

Multiple

Multilevel

Hierarchical

Hybrid

Example (Single):
```cpp
class Parent {
public: void display() { cout << "Parent"; }
};
class Child : public Parent {};
```
🪞 Diamond Problem

Occurs in multiple inheritance when a derived class inherits from two classes that both inherit from the same base.

Solution: Virtual Inheritance
```cpp
class A { public: int x; };
class B : virtual public A {};
class C : virtual public A {};
class D : public B, public C {};  // only one copy of A
```
🧱 11️⃣ Abstract Class & Virtual Function

Abstract Class: Cannot create an object. Contains at least one pure virtual function.

Example:
```cpp
class Shape {
public:
    virtual void draw() = 0; // pure virtual
};
class Circle : public Shape {
public:
    void draw() { cout << "Drawing Circle"; }
};
```

Security impact:
Virtual functions enable runtime binding. Incorrect pointer use may cause data leaks if not handled carefully, but it gives flexibility and polymorphism.

# 🌀 12️⃣ Polymorphism (Many Forms)

Definition: One name, many forms.

| Type         | When decided | Example                                    |
| ------------ | ------------ | ------------------------------------------ |
| Compile-time | At compile   | Function Overloading, Operator Overloading |
| Runtime      | At runtime   | Virtual Function                           |


Example (Runtime Polymorphism):
```cpp
class Animal {
public:
    virtual void sound() { cout << "Animal sound"; }
};
class Dog : public Animal {
public:
    void sound() { cout << "Bark"; }
};
int main() {
    Animal* a = new Dog();
    a->sound();  // Bark
}
```
# ➕ 13️⃣ Function Overloading

Same function name, different parameter list.
```cpp
int add(int a, int b);
double add(double a, double b);
```
# ➕ 14️⃣ Operator Overloading

Allows operators to work with user-defined types.
```cpp
class Complex {
public:
    int r, i;
    Complex(int x=0,int y=0){r=x;i=y;}
    Complex operator+(Complex c) {
        return Complex(r+c.r, i+c.i);
    }
};
```
# 🔒 15️⃣ Encapsulation & Access Specifiers

Encapsulation = wrapping data + functions together and hiding details.

| Specifier | Accessible in class | Derived class | Outside |
| --------- | ------------------- | ------------- | ------- |
| public    | ✅                   | ✅             | ✅       |
| private   | ✅                   | ❌             | ❌       |
| protected | ✅                   | ✅             | ❌       |


Example:
```cpp
class Student {
private:
    int marks;
public:
    void setMarks(int m) { marks = m; }
    int getMarks() { return marks; }
};
```
# ⚠️ 16️⃣ Exception Handling (try–throw–catch)

Used to handle runtime errors safely.

Example:
```cpp
try {
    int a=10, b=0;
    if(b==0) throw "Division by zero!";
    cout << a/b;
}
catch(const char* msg) {
    cout << "Error: " << msg;
}
```
# 💡 SOLVED PROBLEMS
Problem 1: Constructor Overloading

Input:
```cpp
class Student {
public:
    Student() { cout << "Default\n"; }
    Student(string n) { cout << "Name: " << n << endl; }
};
int main() {
    Student s1, s2("Alice");
}
```

Output:
```css
Default
Name: Alice
```
Problem 2: Operator Overloading

Code:
```cpp
class Point {
public:
    int x, y;
    Point(int a, int b) { x=a; y=b; }
    Point operator+(Point p) {
        return Point(x+p.x, y+p.y);
    }
};
int main() {
    Point p1(2,3), p2(4,5);
    Point p3 = p1 + p2;
    cout << p3.x << "," << p3.y;
}
```

Output: 6,8

Problem 3: Exception Handling

Code:
```cpp
int a=5, b=0;
try {
    if(b==0) throw "Cannot divide by zero!";
    cout << a/b;
}
catch(const char* e) {
    cout << e;
}
```

Output: Cannot divide by zero!

Problem 4: Polymorphism

Code:
```cpp
class Animal {
public: virtual void sound(){cout<<"Animal sound";}};
class Dog: public Animal {
public: void sound(){cout<<"Bark";}};
int main(){
    Animal* a=new Dog();
    a->sound();
}
```
```css
Output: Bark
```
| Topic                    | Key Idea                    |
| ------------------------ | --------------------------- |
| OOP                      | Bottom-up, object based     |
| Constructor / Destructor | Auto create/destroy objects |
| Inheritance              | Reuse code                  |
| Polymorphism             | One name, many behaviors    |
| Encapsulation            | Data hiding                 |
| Exception Handling       | Manage runtime errors       |

