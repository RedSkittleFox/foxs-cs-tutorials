# Chapter 3: Functions and Operators

This chapter will teach you how to declare, define and call functions. It will also teach you what operators are.

# What is a function?
Functions are bundles of statements combined in a way to achieve specific outcome. Functions allow us to decrease code repetition and allow code reusability. 

Every function consists of **return type**, **identifier** and optionally **parameters**. Classical functions will take the parameters, transform them and return some other value. In programming it's not always the case. Function can just execute some statements and never return anything.

```cpp
#include <iostream>

void print_fox()
{
    std::cout << "Fox\n";
}

int main()
{
    print_fox();
    return 0;
}
```

# Function in C++

## Overview

As you remember, most of the entities in C++ have both declaration and defintions. Functions are no exceptions. There is a specific *formula* for function definitions and declarations. It goes as follows.

Declaration:
`<return_type> <function_identifier>(<param_1_type> <param_1_identifier>, ..., <param_n_type> <param_n_identifier>)`

Definition:
`<return_type> <function_identifier>(<param_1_type> <param_1_identifier>, ..., <param_n_type> <param_n_identifier>) { }`

The only difference between the declaration and definition is that definition has a body - that `{}` part.

Additional, **parameter identifiers are optional** and are not part of the function **signature - combination of identifier and parameter types**. Return type is excluded on purpose and will be explained why later.

**It's very important to stick to that formula and memorize it! I find many students struggling with function declarations because they only read and copy code, never write it from scratch!**

Let's look closer at the function declaration. `<return_type>` is the type of data that the function will return. The `<return_type>` is the same entity as variable's types. We can later take that data and assign it to the variable with the same type as a return type like so:
```cpp
int get_5()
{
    return 5;
}

int main()
{
    int var = get_5(); // study this line
    return 0;
}
```

Notice how via the usage of `return` keyword we return the value from the function which is later assigned to the variable. There is one additional data type avialable for function return types that isn't avialable for variables - `void`. Using it as the `<return_type>` means that the function doesn't return any value.

TODO: Explain essence of void

TODO: Mention additional trailing return type syntax

TODO: Mention void as the parameter

## Definition, Declaration and Invokation
Let's create our first function.

We want to create a function called *print_int* that will take in some integral value, print it and return 0. Let's look at the formula above and define our function.
Start by deciding on `<return_type>`. In our case it will be `int` because we want to return 0.
The `<function_identifier>` will be our function's name - *print_int*.
There is only one parameter and we know it's an integral value. So the type of parameter will be `int` and the name can be whatever we want - it's only for the usage within the function.

```cpp
// <return_type> <function_identifier>(<param_1_type> <param_1_identifier>)
int print_int(int some_value)
{
    std::cout << some_value << '\n'; // Print our value
    return 0; // Return 0
}
```
Naturally all the statements belonging to function are stored inside function's body marked by `{}` brackets.


Now let's use our function!
```cpp
int main()
{
    int v1 = print_int(1); // passing literal value
    int a = 10;
    int v1 = print_int(a); // passing value stored in a
    return 0;
}
```
By now you might have noticed, that to call the function you have to pass parameters to it by opening `()` braces and passing all parameter separated by commas.

Additionally, function parameters look awfuly simillar to regular variables. This is because they are variables! By declaring them as a part of function signature we just tell the compiler to automatically set their values to whatever we've passed as a value during function call (and obviously before function body gets executed).
`print_int(1)` will set the value of `some_value` to 1 and then execute statements inside function body. 
`print_int(a)` will be equivalent to `some_value = a` and then executing the statements bundled in a function.

## Examples

Function called *print_age* that **returns nothing** and takes in user's age and then print's it.
```cpp
#include <iostream>

// Notice that the return type is void
void print_age(int age)
{
    std::cout << "Marcin is " << age << " years old!\n";
}

int main()
{
    print_age(20);
    return 0;
}
```
-----
Function called *print_pair* that prints the pair of two real numbers and returns the first one.
```cpp
#include <iostream>

float print_pair(float a, float b)
{
    std::cout << a << " " << b << "\n";
    return a;
}

int main()
{
    float my_favourite_real_number = 3.141592;
    print_pair(1.2, my_favourite_real_number); 
    // notice that we didn't assign the return value to any variable
    // and multiple parameters are separated by a comma
    
    return 0;
}
```
-----
Function that prints *Foxes are better than capybaras*.
```cpp
#include <iostream>

void foxes_are_better()
{
    std::cout << "Foxes are better than capybaras\n";
}

int main()
{
    foxes_are_better();
    return 0;
}
```
It's important to note, that in order to call a function you have to always do it using `()` operator. Even whenthere are no parameters, it has to be present. Doing just 
```cpp
int main()
{
    foxes_are_better;
    return 0;
}
```
**will not** call the function but instead give you a *function pointer*, something that will be discussed in later chapter.

-----
**Pronounce** (read) the following function declarations.
```cpp
/*1*/   int foo();
/*2*/   void area(int a, int b);
/*3*/   float fox_in_a_box(float, int);
```

1. Function returning `int`, identified as *foo*, accepting zero arguments.
2. Function returning `void`, identified as *area*, accepting two arguments of type `int` and `float`. 
3. Function returning `float`, identified as *fox_in_a_box*, accepting two arguments of type `float` and `int`.

It's important to learn how to read and interpret the signature correctly from the definition above.

# Operators
Now that we know what a function is, we can talk about function operators - functions with special invocation syntax.

Look at this piece of code.
```cpp
#include <iostream>

int main()
{
    int a = 5;
    int b = 4;
    
    int a_mul_b = a * b;
    int a_plus_b = a + b;

    std::cout << "a * b = " << a_mul_b << "\n";
    std::cout << "a + b = " << a_plus_b << "\n";
}
```

Operators are builtin functions that can be invoked by applying a special character to an object(s) - something that has a type and lies in memory.

## The Essence 

**Disclaimer: In the next section to fully present what operators are I'm going to present you with new variable types - references. They are created by taking a type and adding & symbol to it: `int&` - int reference. What they truly mean is going to be discussed in more advanced series. For now just treat them as a regular type - in the case above it would be `int`.**

**Disclaimer: LHS and RHS stand for left-hand-side and right-hand-side**.

Operators can be invoked by putting operator's token in appriopriate context. In the case above.
```cpp
int a = 5;
```
The assignment operator above has syntax as follows `int& operator=(int& lhs, int rhs)`. The above is equivalent to
```cpp
// this is a pseudo code
int a;
operator=(a, 5); 
```

Likewise 
```cpp
int a_mul_b = a * b;
```
can be viewed as
```cpp
// this is a pseudo code
int a_mul_b;
operator=(a_mul_b, operator+(a, b));
```
First we invoke `operator+` that returns the sum of *a* and *b*. After that we set the *lhs* parameter of `operator=` to `a_mul_b` and *rhs* parameter to the return value of `a + b`. Now you can see why the operator were created. Instead of writing huge chains of functions we can simply write what we want in the *familiar*, mathematical notation.

# Arithmetic Operators
As mentioned above, the called operator function is determined basesd on context. Multiplying two integers will call a different operator than multiplying a matrix by an integer. 
For builtin *arithmetic types* (`int`, `float`, `double` etc.) however, operators will behave as expected.

Here is a list of select fiew **arithmetic** operators, example usage and signatures. Comparison, logical and bitwise operators will be discussed in later chapters.

| Name               	| Description                                            	| Syntax   	| Function Signature for `int` 	| Example                   	|
|--------------------	|--------------------------------------------------------	|----------	|------------------------------	|---------------------------	|
| Addition           	| Return the sum of two numbers                          	| `a + b`  	| `int operator+(int, int)`    	| `std::cout << 1 + 2;`     	|
| Subtraction        	| Returns the difference of two numbers                  	| `a - b`  	| `int operator-(int, int)`    	| `int c = 2 - 1;`          	|
| Multiplication     	| Returns the result of multiplying two numbers together 	| `a * b`  	| `int operator*(int, int)`    	| `int c = 2 * a;`          	|
| Modulo             	| Returns the integral reminder of two integers          	| `a % b`  	| `int operator%(int, int)`    	| `std::cout << a % 2;`     	|
| Addition assigment 	| Adds a number to the left hand side.                   	| `a += 5` 	| `int& operator+=(int&, int)` 	| `a += 5; std::cout << a;` 	|

The complete list can be found [here](https://en.wikipedia.org/wiki/Operators_in_C_and_C).

Notice the `operator+=`, instead of writing
```cpp
a = a + b;
```
you can write
```cpp
a += b;
```
Other arithmetic operators also have *assigment* variants avialable.

## Fiew words on Operator Overloading
It is possible to define custom behaviour for most operators for UDTs. The process is called *operator overloading*. It is tightly related to *function overloading*. Both of which will be discussed in more advanced series. It is not possible to add new operators (new symbols). 

## Examples
Create a function that calculates the area of the square based on it's side's length.
```cpp
#include <iostream>

// notice the return and parameter's types
float square_area(float sides_length) 
{
    return sides_length * sides_length; // usage of operator*(float, float)
}

int main()
{
    float area = square_area(5.5);

    std::cout << "The area of the square with the side of length 5.5 is << " << area << "\n";
    return 0;
}
```
-----
Create a function that calculates the sum of 3 integers.
```cpp
#include <iostream>

// notice the return and parameter's types
int sum(int a, int b, int c) 
{
    return a + b + c; // notice chained operator+
}

int main()
{
    std::cout << "1 + 2 + 3 = " << sum(1, 2, 3) << "\n";
    return 0;
}
```
-----
Create a function that calculates the reminder of division by two and then add the result of it's call to the variable storing the same value as passed parameter.

```cpp
#include <iostream>

int reminder_two(int i)
{
    return i % 2; // modulo operator
}

int main()
{
    int a = 5; // assignment operator
    a += reminder_two(a); // operator add-assign
    std::cout << "5 + (5 mod 2) = " << a << "\n";
    return 0;
}
```

# Distance Between Points - Exercise 

Create a function that calculates a distance between two 3D points. Think about how the point is defined - group of 3 real numbers. Pick the proper return type. Do some research and find a function in *C++'s Standard Library* that can calculate the square root for you.

# Distance Between Points - Solution

```cpp
#include <iostream>
#include <cmath> // std::sqrt

float distance(float x1, float y1, float z1, float x2, float y2, float z2)
{
    // Calculate distances between points
    float dif_x = x1 - x2;
    float dif_y = y1 - y2;
    float dif_z = z1 - z2;

    // Compute squares 
    dif_x *= dif_x;
    dif_y *= dif_y;
    dif_z *= dif_z;

    // Compute sum
    float square_sum = dif_x + dif_y + dif_z;

    // Return square root
    return std::sqrt(square_sum);
};

int main()
{
    std::cout << "The distance between (1.5, 4.3, 2.2) and (5.3, -3.2, 5.4) is " 
        << distance(1.5, 4.3, 2.2, 5.3, -3.2, 5.4) << "\n";

    return 0;
}
```

# Summary
* Functions can be declared and defined by following the syntax rules
* Functions can be called via `()` operator
* Accessing the function without `()` yelds a function pointer
* Functions allow for the code to be reused
* Functions have a return type, identifier and optionally parameters
* Functions that don't return any value have `void` as the return type
* `return` keyword is used to return the value for the function
* Operators are functions with a funny syntax
* Operators for builtin types are builtin functions/
* Functions can be overloaded
* Operators can be overloaded - customised for UDTs