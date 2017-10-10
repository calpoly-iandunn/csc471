---
layout: page
active: lectures
title: "Lecture 14: C++ 1"
auto-title: true
---

## Basics

C++ is in some ways a combination of Java and C.
It has syntax and a lot of other features borrowed from C, but also supports object-oriented programming similar to Java.
One interesting aspect of C++ programming is that it is (typically, for most use cases and with a few small syntax changes) backwards compatibile with C.
You can, for all intents and purposes, write a program in C and use a C++ compiler to compile it.
We could do that for our raytracer, but object oriented programming is incredibly useful for writing a raytracer, so we will want to make use of C++ objects.

C++ objects are similar to C structs, but they allow you to define both data and behavior, unlike C structs which only support data definitions.
The behavior of a C++ object takes the form of member functions, which should be familiar to you as a Java programmer.

Take a look at `Vector.h` (sample files listed at the bottom of notes) for an example of a C++ class.

First let's look at our constructors and destructors:

```cpp
Vector();                 // default constructor
Vector(Vector *);         // constructor
Vector(const Vector &);   // copy constructor
~Vector();                // destructor
```

Constructors are special member functions used to create instances of our class.
We can have multiple constructors if there are multiple ways to create instances.
In the case of our `Vector` class, we declare a default constructor and two other constructors to give three ways to make a `Vector`.
You might be confused about the use of the `&` symbol in our third constructor, but we'll talk about this in a second - it's a C++ concept called a **reference**.

Finally, we have a destructor.
This function is responsible for destroying the class when it's time for it to be deallocated.

## References

```cpp
void swap(int *a, int *b)
{
    int temp = *a;
    *a = *b;
    *b = temp;
}

// elsewhere

int x, y;
swap(&x, &y);
```

```cpp
void swap(int &a, int &b)
{
    int temp = a;
    a = b;
    b = temp;
}

// elsewhere

int x, y;
swap(x, y);
```


## Inheritance

Check out `GeomObject.h`.

Syntax for declaring inheritance:

```cpp
class GeomObject
{
    // ...
};

class Sphere : public GeomObject
{
    // ...
};
```


## Memory Allocation

If we want to create instances of our classes, there are two ways to do it.
We can either create them on the stack (limited to current scope) or allocate them on the heap.

```cpp
// Stack allocation
{
    Vector v1;
    Vector v2 = v1;
    v1.p_x = 3.0;
} // v1 and v2 go "out of scope" here and are deallocated
```

```cpp
// Heap allocation
{
    Sphere *sphere = new Sphere();
    Sphere *other = new Sphere();

    scene->AddGeomObject(sphere);

    delete other; // 'other' is deallocated now
} // The pointers 'sphere' and 'other' go out of scope, but what they point to is not deallocated.
// The Sphere instance we created on the first line still exists, and 'scene' can still use it
```

Note: Virtual functions only work on pointers!!! They don't have to be heap-allocated

Here, `new` and `delete` replace the C usage of `malloc` and `free`.
There should be no `malloc`s or `free`s anywhere in your code!

Note that to allocate arrays of something (instead of just a single copy), there are special commands:

```cpp
int * my_int_array = new int[10];
my_int_array[4] = 2;
delete[] my_int_array;
```


## Example Files

- [Vector.h](https://github.com/iondune/csc471-lecturecode/blob/master/Vector.h)
- [Vector.cpp](https://github.com/iondune/csc471-lecturecode/blob/master/Vector.cpp)
- [GeomObject.h](https://github.com/iondune/csc471-lecturecode/blob/master/GeomObject.h)

## References

- [Rule of Three](http://en.cppreference.com/w/cpp/language/rule_of_three)
  - Don't worry about the "Rule of Five" - we will cover this laster in the quarter
