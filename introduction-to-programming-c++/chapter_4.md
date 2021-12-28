# Chapter 4: Conditional Statements - Boolean's Algebra and Loops

In this chapter you will learn how to declare conditional statements and the basics of Boolean's algebra.

# Boolean's Algebra and C++
Boolean algebra is the branch of algebra in which the values of the variables are either true or false - usually represented by 1 and 0. There are 3 basic operations - conjunction, disjunction and negation. 

| Logical Operation 	| Operator 	| Definition 	| C++ Operator 	| Example 	|
|---	|---	|---	|---	|---	|
| Conjunction 	| AND 	| x AND y = 1 if x = y = 1, x AND y = 0 otherwise 	| `&&` 	| `bool b = 1 && 0;` 	|
| Disjunction 	| OR 	| x OR y = 0 if x = y = 0, x OR y = 1 otherwise  	| `\|\|` 	| `bool b = 1 \|\| 0;` 	|
| Negation 	| NOT 	| NOT x = 1 if x = 0, NOT x = 0 if x = 1 	| `!` 	| `bool b = !1;` 	|

## Truth Tables

| x 	| y 	| x && y 	| x \|\| y 	|
|---	|---	|---	|---	|
| 0 	| 0 	| 0 	| 0 	|
| 1 	| 0 	| 0 	| 1 	|
| 0 	| 1 	| 0 	| 1 	|
| 1 	| 1 	| 1 	| 1 	|

| x 	| !x 	|
|---	|---	|
| 0 	| 1 	|
| 1 	| 0 	|

## Boolean Type and Literals
C++ provides the data type - `bool` that can store results of mentioned operations. Additionaly C++ provides two named values - `true` and `false` which have the underlying values of `1` and `0` respectively. It's important to note that any integral type can be casted down to `bool`. Casting rules are as follow - `0` is casted to `false`. Everything else is casted to `true`. 

// TODO: Check negative numbers?

```cpp
int main()
{
    bool a = 0;
    bool b = 1;
    bool c = false;
    bool d = true;
    return 0;
}
```

# Comparison Operators
Additionally C++ provides these comparison operators for all built-in arithmetic (excludting some for pointers) types.

| Operator Name 	| Syntax 	| Function Signature for `int` 	| Example 	|
|---	|---	|---	|---	|
| Equal to 	| a == b 	| `bool operator==(int, int)` 	| `std::cout << (1 == 2);` 	|
| Not equal to 	| a != b 	| `bool operator!=(int, int)` 	| `std::cout << (1 != 2);` 	|
| Greater than 	| a > b 	| `bool operator>(int, int)` 	| `std::cout << (1 > 2);` 	|
| Less than 	| a < b 	| `bool operator<(int, int)` 	| `std::cout << (1 < 2);` 	|
| Greater than or equal to 	| a >= b 	| `bool operator>=(int, int)` 	| `std::cout << (1 >= 2);` 	|
| Less than or equal to 	| a <= b 	| `bool operator<=(int, int)` 	| `std::cout << (1 <= 2);` 	|
Notice, how all comparison operators return `bool`.

```cpp
#include <iostream>

int main()
{
    int a = 10;
    int b = 15;

    bool is_a_greater = a > b;
    std::cout << is_a_greater;
    return 0;
}
```

The value of the statement `a > b` is `0` and is later assigned to the variable of type `bool` *is_a_greater*.

# Conditional Statmenets
We know how to write `true-false` statements using Boolean algebra and we know how to compare values. It's time to use the results of those operation.

## The `if`

The syntax for conditional statements is as follows:

`if( <condition> ) <expression>;`

`if( <condition> ) { <expression_1>; ...; <expression_n>; }`

Copy the following code and run it.
```cpp
#include <iostream>

int main()
{
    int a = 5;
    int b = 6;

    if(a < b)
    {
        std::cout << "a is lesser than b\n";
    }

    if(a > b)
    {
        std::cout << "a is greater than b\n";
    }

    if(a == b)
    {
        std::cout << "a equals b\n";
    }
}
```

## The `if-else`
In the example above we can see that conditions are mutualy exclusive, if a is lesser than b, it won't be equal or greater than b. We can rewrite the statement above to use `if-else`.

This is the syntax.

`if( <condition> ) { ... } 
else if ( <condition> ) { ... }
else {...}`

```cpp
#include <iostream>

int main()
{
    int a = 5;
    int b = 6;

    if(a < b)
    {
        std::cout << "a is lesser than b\n";
    }
    else if(a > b)
    {
        std::cout << "b is greater than a\n";
    }
    else // if a is not smaller or greater than b <=> a == b
    {
        std::cout << "a equals b\n";
    }
}
```

Be careful though. Notice that if one of the conditions is met, other won't be tested. 

```cpp
#include <iostream>

int main()
{
    int a = 5;
    int b = 6;

    if(a > 1)
        std::cout << "a > 1\n";
    else if(a > 2)
        std::cout << "a > 2\n";

    if(b > 1)
        std::cout << "b > 1\n";
    
    if(b > 2)
        std::cout << "b > 2\n";
}
```

# Loops
We can tell the program to repeat some statements until the condition is met.

## The `while` loop

`while( <condition> ) { ... }`

The program below will print *fox* ten times.

```cpp
#include <iostream>

int main()
{
    int i = 0;
    while(i < 10)
    {
        std::cout << "fox\n";
        i += 1;
    }
}
```

## The `for` loop

`while( <declaration>; <condition>; <modifier> ) { ... }`

We can simplify the code above by replacing the `while` loop with the `for` loop.

```cpp
#include <iostream>

int main()
{
    for(int i = 0; i < 10; i += 1)
        std::cout << "fox\n";
    
}
```

Notice how the `<modifier>` which was previously inside the while loop is now inside statement declaration. It behaves identically though and will be *invoked* at the end of every iteration.

## The `do-while` loop

`do {...} while( <condition> );`

This loop is allows us to delay the condition check to be after the iteration, rather than before. 

```cpp
#include <iostream>

int main()
{

    int i = 0;    
    do
    {
        std::cout << "condition checked after **previous** iteration";
    }
    while(i != 0);
}
```
