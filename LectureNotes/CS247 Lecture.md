# CS247 Lecture

## Lecture 1 May 6 2019

Prof Robert Hackman

SE is to improve quality, productivity, larger systems, evolvability

More real world focus 

ADT Design, -- productivity 

Modules and Interfaces

Exceptions

Interface Specifications

OO design Principles 

Design Patterns 

UML modelling -- productivity 

Generic Programming (Templates, STL)

Testing/Debugging 

Monday 3:30 - 5 

12 Hours of Module Design

12 OO

Thinking in C++ need to read those 

15% Assignments 

A1 May 24

A2 June 14 

A3 July 30 

5% each 

Between A2 and A3 are projects 

Project 2 or 3 people 

Group of 3 best 

July 19-21 do the demo 

must be able to run and compile linux.students.cs.uwaterloo.ca

June 28/July 16 demo projects

Midterm 20% Final 50%

Tutorials, introduce tools and more examples, discussing assignment
 
C++ has inheritance 

Private and Public 

MyClass C in C++: 

Default Constructor

Riase level of abstraction, interfaces 

Reuse 

Modularity 

Information Hiding

Polymorphism 

## ADT Design 

Abstract Data type, user defined, implementation might vary but same methods 

Bundles together 

1. Range of Valid Values/Data
2. Functions over those values 

Ideally use help of compiler to enforce users to use it properly 

* ADT allow us to employ outside in design 

Basically encapsulating a convoluted data and make it clearer for the client to use it, just knowing the interface, not how it's done 

Client - Interface - Implementation Details 

```
#include <iostream>

using namespace std

int main() {
    cout << "Enter a rational(a/b): ";
    Rational r, p, q;
    cin >> r, 
    cout << "Enter a ratioanl(a/b):";
    cin >> q;
    cout << r;
    p = q + r;
    cout << p;
    cout << q / p;
}
```

default constructor? No params 

overload input operator with istream& and a rational&, mutate that object

overload output operator with ostream& and a rational& or not (should const) faster, no copy 

can't copy the streams 

overload additional operators with rationals 

pass rationals const reference 

return by value for rational -- created a new value 

assignment operator -- copy & move 

division opereator 

copy constructor Rational z(q) 

big 3:

destructor, copy constructor, copy assignment operator -- exception free 












