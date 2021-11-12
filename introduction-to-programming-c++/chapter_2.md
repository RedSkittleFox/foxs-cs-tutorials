# Chapter 2: Variables

This chapter will teach you how to declare, define and use variables.

# Declaration and Definition - important terminology
Those two concepts are intrinsic to all C++ entities concept. Almost every entity can be declared and defined. Sometimes the definition is the declaration. Declaration is telling the compiler that something entity exists somewhere in the code. Definition is telling the compiler what the entity is. Declaration has to be avialable before the entity is used in the compiled code. Defintion just has to be avialable in one way or another before the code gets executed - either as a source code or in a form of library as a machine code.

I'm going to provide this example to give you the rough idea. It's going to be explained in depth in later chapters.
```cpp
// File a
int a; // declaration

// File b
int a = 5; // definition
```

# Memory and Size - important terminology
Size (or capacity) of the computer memory is measured in `Byte`s. `Byte` is made out of 8 **bit**s. **Bit** is the smallest memory capacity unit. It can store a value of either 0 or 1 (false or true). You can think about a `Byte` as the line of 8 boxes which can have something inside or not. This means that a single `Byte` can store 2 ^ 8 = 256 unique values.

| 0 	| 1 	| 0 	| 1 	| 0 	| 1 	| 1 	| 1 	|
|---	|---	|---	|---	|---	|---	|---	|---	|

Every single 0 and 1 is the **bit**. The whole group above is the `Byte`.

Now the memory can be viewed as the very long list of `Byte`s. Each `Byte` in the memory can be refered to via the *address* - an integer from 0 up to the capacity of the memory.

| Address:  	| 0        	| 1           | 2        	| 3        	| 4        	| 5        	|
|-----------	|----------	|------------ |----------	|----------	|----------	|----------	|
| Value:    	| 01001000 	| 11001100 	  | 00001111 	| 10101001 	| 11000011 	| 11000011 	|

Now we can say: The `Byte` at **address 1** stores the value `11001100`.
The `Byte`s at **address 4 and 5** store the value `11000011`.

The address will be in the future represented by a special kind of type called *pointer*. It will be discussed in depth in later chapter.

# The Variable

Copy the code below and run it.

```cpp
#include <iostream>

int main()
{
    int a;
    a = 5;
    
    std::cout << "a = " << a << '\n';
    
    return 0;
}
```

```cpp
int a;
```

Here we declare and define a new variable with the **identifier** *a* and of **type** `int`.
The declaratio of variable **must** consist of at least those two things.  
The **identifier** is just the user-specified name that we will be later refering to.
The **type** describes what the variable will be storing. Types are used both by a compiler and programmer to tell what kind of value the variable holds. Every variable takes up the physical space in your computer's memory and the type of the variable defines how much of the memory it occupies. From the statements above we can deduce that every variable has two intrinsic properties - **unique address in the memory** and **size**.

-----

```cpp
a = 5;
```

Here we assign the value of **5** to the variable **a** of type `int`. Let's try assigning a string to it. Try replacing the value of **5** with `"I like foxes"` and try to run the program.

```cpp
#include <iostream>

int main()
{
    int a;
    a = "I like foxes";
    
    std::cout << "a = " << a << '\n';
    
    return 0;
}
```

The program has failed to compile. This means that in the variable we can store only the values of the same type as the variable.

# Types
There are two kinds of types in C++ - **Builtin types** (also known as fundamental)  and **UDT** (*User Defined Types*). For now we are going to solely focus on builtin types. In future guides UDTs and the whole concept of OOP - *Object Oriented Programming* will be discussed.

## Builtin Types
The full list of builtin types can be seen [here](https://en.cppreference.com/w/cpp/language/types). Here is a table of most common ones, their sizes and usage and value range. Keep in mind that the size might vary depending on a platform (Windows or linux) you are using.

// TODO: Type entropy

| Type          	| Size (Bytes) 	| Usage                         	| Value Range           	| Possible Unique Different Values 	|
|---------------	|--------------	|-------------------------------	|-----------------------	|----------------------------------	|
| float         	| 4            	| real numbers                  	| (too big to put here) 	|                                  	|
| double        	| 8            	| real numbers                  	| (too big to put here) 	|                                  	|
| int           	| 4            	| integral numbers              	| -2 ^ 16 to 2 ^ 16 - 1 	| 2 ^ 32                           	|
| short         	| 2            	| integral numbers              	| -2 ^ 8 to 2 ^ 8 - 1   	| 2 ^ 16                           	|
| unsigned int  	| 4            	| natural numbers               	| 0 to 2 ^ 32 - 1       	| 2 ^ 32                           	|
| unigned short 	| 2            	| natural numbers               	| 0 to 2 ^ 16 - 1       	| 2 ^ 16                           	|
| char          	| 1            	| integral numbers / characters 	| -128 to 127           	| 2 ^ 8                            	|

Notice the usage of `unsigned` keyword. It *shifts* the range of values however it doesn't change the total amount of unique values that can be stored in a variable of that type.

Now you can clearly see that different types can store the same type of value however they are limited by their size in memory on the range of values they can store. For example `int` can store bigger values than `short`.

## Hello Age! - Exercise
Create a variable, give it a proper name and assign your age to it. Then print your age using it. Make sure to pick the proper type! 

## Hello Age! - Solution
```cpp
#include <iostream>

int main()
{
    int age = 20;
    std::cout << "Hello Age!\n"
        << "I'm " << age << " years old!\n";
    return 0;
}
```

# Summary
* To declare variable you need to specify it's `type` and **identifier**.
* Every variable has a type, size and **an address in the physical memory**.
* Different types can store different value types and have different capacities.
* Memory is made out of `Byte`s. `Byte` is made out of 8 **bit**s.