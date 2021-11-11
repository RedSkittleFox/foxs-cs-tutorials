# Chapter 1: *Hello World!*

This chapter will teach you how to write, compile and run a simple program.

# Getting started - the IDE
Many tutorials will encourage you to install one of many popular IDEs such as Visual Studio, CLion and Code Blocks. Usage of those IDEs often requires user to create some sort of project and compiler configuration. Build systems and compiler configurations are not part of the scope of this tutorial series and will be discussed in future, more advanced series. 

Unless you are familiar with one of those environments I encourage you to use [onlinegdb.com](https://www.onlinegdb.com/). It's a website that will allow you to simply write and run a program without worrying about anything. In order to get started open the link ad set your language (top right corner) to C++17.

# Compilation Process
The process itself is going to be explained later. For now just remember. Compiling is taking the code programmer wrote - *source code* and converting it to the code that the computer can understand - usually *machine code*. This is a heavily simplified description.

# Hello World! - your first program

For now copy and paste this fragment of code and run it.
```cpp
#include <iostream>

int main()
{
    std::cout << "Hello World!\n";
    return 0;
}
```

The program printed `Hello World!` in the console. Now let's slowly analyze it.

------

```cpp
#include <iostream>
```
Most programming languages come with a set built-in of utilities to help programmers accomplish simple tasks without making them write commonly used code. Those utilities together are called **Standard Library** and include basic data structures, algorithms, console IO mechanisms etc. 

In C++ standard library is divided into numerous submodules which can be included using a `#include <standard library module>` *preprocessor* directive. Both preprocessor and classic C++ *linking* model will be discussed in later chapters. For now let's focus on the statement above. We know that we include a module from stanard library called *iostream* which stands for *input and output stream*. It's going to allow us to use `std::cout` object later.

------

```cpp
int main()
{
    ...
}
```

This is the so called *entry point*. Executing the application is equivalent to executing this function. You will learn more about functions in the next chapter. Right now all you need to know is that the code gets executed from left to right, top to bottom, statement by statement. 

Each statement is just some code followed by `;`. For instance:
```cpp
std::cout << "Hello World\n"; // first statement

int a 
    = 5; // second statement, what this means will be revealed later
```
As you can see, white spaces don't mean anything in terms of statement declarations and can be placed as see fit. It's advised to stick to same coding style accross your whole project to increase readability.

As you can see I also wrote some *comments*.
There are two types of comments in C++ - single-line and multi-line comments. Single-line comments comment-out everything till the new line. Multiline comments comment out everything between the comment markers.
```cpp
// this is a single line comment
this isn't commented out!

/* this is
a multiline
comment */
```

------

```cpp
std::cout << "Hello World!\n";
```

Now this statement might look a bit strange, but for now I won't be explaining how and why it works. All you need to know that you `std::` is the *namespace*, `cout` is the *handle to the console* and by using `<<` operator we can *stream* the data to the console like above.

The pair of `"` symbols defines the string - some text we want to deal with in the program. This will be discussed in details in later chapter.

Fiew examples:
```cpp
std::cout << "This is a string.";   // prints out a string
std::cout << 1;                     // prints out a whole number
std::cout << 1.2;                   // prints out a real number
```

Additionally `<<` operator can be *chained together*. So instead of writing the above, one could write simply this.
```cpp
std::cout << "This is a string."
    << 1                     
    << 1.2;                   
```
It's important to note here, that at the end of each line there is no `;` marking the end of the statement. The whole `std::cout << "This is a string." << 1 << 1.2;` is then just a single statement.

------

```cpp
return 0;
```

Every function must return a value. That's the nature of a function. Because `main` is a function it must return a value. Functions are gonna be explained indepth in later chapters. For now just remember that values returned by the `main` function are program status indicators. For instance:
* `0` - program succeeded
* `-1` - some error occured.

# ASCII and special characters
ASCII is a 7-bit character coding system. It basically assigns a value from 0 to 127 to every letter and most common symbols of english alphabet. For instance

| Character 	| Decimal Value 	|
|-----------	|---------------	|
| A         	| 65            	|
| a         	| 97            	|
| b         	| 98            	|
| [         	| 91            	|
| ]         	| 93            	|

You can view the whole list [here](https://en.wikipedia.org/wiki/ASCII#Printable_characters).

You might have a strange `\n` symbol at the end of `"Hello World!\n"`. This is one of special characters meaning *start a new line here*. There are fiew more like this but we are gonna look deeper into them in the upcoming chapaters.

# Hello Me! - Exercise

Now try to modify the code above to achieve the following output:
```
Hello Me!
My name is Marcin.
I'm 20 years old.
I like Foxes :)
```
Try outputing the age as a whole number, rather than the part of a string.
You can ofcoures change this to the information about you ;)

# Hello Me! - Solution

```cpp
#include <iostream>

int main()
{
    std::cout << "Hello Me!\n"; // notice the '\n' symbol inserting new line
    std::cout << "My name is Marcin.\n";
    std::cout << "I'm " << 20 << " years old.\n" // here we used << operator chaining
        << "I like Foxes :)\n";
    return 0;
}
```

# Summary
* `main` function is the entry point
* `#include <some standard library>` is used to include standard libraries
* do `std::cout << something` to print something to the console