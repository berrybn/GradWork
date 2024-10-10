# [[AOOP_Text.pdf]]
# Book Notes
A C++ program will have the following structure:
## Library inclusions 
1. `#include <systemlib>`
2. `#include "privatelib"`
3. We will NOT use `namespace std;` usually, because it causes problems later -- use good coding form. `std::cin`, `std::cout`, `std::endl`, `std::setw()`
## Program level definitions 
4. variable definitions, function declarations
	1. these apply to the program as a whole
	2. could declare as a constant variable type, one that does not change: `const type name = value;`
5. function prototypes 
	1. a declaration that tells the compiler the information it needs to know about a function to generate the proper code when that function is called.
	2.  use to set function parameters and function type
	3. *like the variable version of a function*
6. main function
	1. the starting point for the computation
7. Function declarations to be used in the main
## Example - a table that prints the first 12 $N^2$ and $2^N$
This program generates a table comparing the values of $N^2$ and $2^N$ for various values of N. 
```cpp
#include <iostream>
#include <iomanip>
#include "genlib.h"

//constants setting the starting and ending value for the table
const int LOWER_LIMIT = 0;
const int UPPER_LIMIT = 12;

//set a function prototype, to be defined later.
int RaiseIntToPower(int n, int k);

// main() is where program execution begins.
int main() { 
	std::cout << " | 2 | N" << std::endl;
	std::cout << " N | N | 2" << std::endl;
	std::cout << "----+-----+------" << std::endl;```
- Tables require a layout using `std::cout`
- A `for` loop is used to generate the table of values. 
- We use $n$ to represent some value $\leq 12$ (the `UPPER_LIMIT` constant), and increment $n$ along those lines, until $n$ isn't $\leq 12$. 
- This portion of the for loop also prints the values of $n$, and $N^2$, $2^N$, which are found using the `int RaiseToIntPower(int n, int k)` function.
```cpp	
	for(int n = LOWER_LIMIT; n <= UPPER_LIMIT; n++){
	std::cout<< std::setw(3)<<n<<" |";
	std::cout<<std::setw(3)<<RaiseIntToPower(n,2)<<" |";
	std::cout<<std::setw(5)<<RaiseIntToPower(2,n)<<std::endl;
	}
   return 0;
}```
- Here we define `RaiseIntToPower` function explicitly. 
- We define a variable `result`, and set it = 1. 
- Then for each we initialize a `for` loop with iterator $i$, and we increment $i$ based on if $i<k$ (the power)
- During the loop we multiply each n by itself and store it in result`result*=n`. 
- Function returns `result` This can create a list of values based on how the `RaiseIntToPower` function is called 
	- The code explicitly uses the parameters `RaiseIntToPower(2, n)` and `RaiseIntToPower(n, 2)` to represent $N^2$ and $2^N$ respectively
```cpp
int RaiseIntToPower (int n, int k){
	int result;
	result = 1;
	for(int i = 0; i<k;i++){
	result *=n; //
	}
	return result;
}

```

## Variables and Types

const variables are given ALL_CAPS
Functions are given w uppercase letters

We declare types to establish what kind of variable is being used. 

local variables

global variables - declaration appears outside any function definition, the scope of the variable is the remainder of the file in which it is declared

| Keyword | Type                  | Storage |
| ------- | --------------------- | ------- |
| bool    | Boolean               | 1 byte  |
| char    | Character             | 8 bits  |
| int     | Integer               | 32 bits |
| float   | Floating point        | 32 bits |
| double  | Double floating point | 64 bits |
| void    | Valueless             |         |
Note: Strings are not inherent types and their library must be included in order to declare a string. `#include <string>`

Statically typed vs Dynamically typed: 
## Input/Output streams
`std::cin>> value;` allows the user to give the computer information
`std::cout<<"statement";` allows the user to give the computer information

## Selection Structures
- Algorithm: A procedure for solving a problem in terms of

- the actions to execute
- the order in which the actions will execute

- Pseudocode: "fake" code

- describes the action statments in English
- helps a programmer "think out" the problem and solution but does not execute

- Flow of Control/Execution: implemented with three basic types of structures

- Sequential: default mode; Executed line by line, one right after the other
- Selection: decisions, branching; When there are 2 or more alternatives. Three types:

- if
- if...else
- switch

- Repetition: used for looping, or repeating a section of code multiple times. Three types:

- while
- do...while
- for

- True and False

- Statements that are executed are dependent on certain conditions that are evaluated either true or false.
- Condition represented by logical (Boolean) expression - can be true or false
- Condition met if evaluates to true
- **Key:** Any C++ expression taht evaluates to a value can be interpreted as a true/false condition.

- An expression that evaluates to 0 is **false**.
- An expression that evaluates to a non-zero value is **true**.
## Loops
while(expression)
	statement;
expression - a condition tested to determine whether the statement is executed. 



Classes allow programmers to create operators for abstract mathematical structures. 

# CLASS 3
the difference between getline and cin 
to read the entire line from the user use getline. cin will only work up to the whitespace

function overloading - two functions with teh same name as long as they have different arguments

Assignment 1 
Write a program that prompts the user for their first name, last name, address, and phone number
Store the information 

Write a procedure reverse that reverses the sequence of elements in a vector

Given a sequence of values in a vector, we want to output the reverse order of the vector
We need the size of the vector
we need to cycle through the vector components, each index $\{x_0,x_1,x_2,x_3...\}$
is there away to compare indexes of the vector?
We can:
1. create a new empty vector
2. create a vector with n copies of 0
3. create a vector with n copies of a value k
4. add a value k to the end of the vector << we might need this
5. get the element at index i << we might need this
6. check size of the vector << we need this
If i have the size of the vector, I can know how many items are in the vector

Write a function merge_sorted that merges two sorted vectors (as a challenge, add the sorted component)

Write a short program that creates a map of menu items 




# Git
git clone - get a copy of the repo on your computer. Creates a directory within the folder

git log - shows the changes over commits

q to exit git log

git - version control system
allows to track changes made to a file as we develop it
allows many programmers to work on a common set of files

server computer - home of the repo
computer a sends info to the remote repo, computer b sends info to the remote 

git and github are not the same thing - github is where you post the repo. git is an open source software

Modified means saved file, but not committed - saved changes 
Staged means you have marked the file to be in the next commit
add all files to the staging area "git add \<filename\>"

committed means the changes you have made have been recorded
use "git commit"

git config --list to show username and email

changes to be committed: staging area
git diff will show changes you've made before committing

github can host the remote repository - a repo accessible through a network

pro git book

2
3
5
7
11
13

prime is only divisible by itself and 1.

# Class 5
initializing values, references

`#pragma once`
compiler based - not all compiles support it
if the header file is duplicated accidentally it might thing its a diff file
not best practice - with large code, version control system merge - will include and compile twice bc in diff directories

providing initial values to variables - declare THEN initialize

uniform initialization - curly brackets
don't need the equal sign, but don't use parentheses - those act as parameters

`auto` keyword that can be used in lieu of typing - l a z i n e s s
will deduce the variable type
can't use it without initializing the variable

quadratic equation example

structured binding
declare multiple variables initialized from a tuple or struct

`auto[x_coord,y_coord] =p` stores information so that it can be manipulated, still auto deducing the type

reference - an alias for a named variable
pass by reference - means that 

pointer - stores the memory address - dereference the pointer?
printing a pointer will print the memory address

passing by reference to x vs making a copy of the variable and passing a copy

[[AOOPCookBook]]


C++ makes a true copy - if we inted to have a reference instead of a copy 

swap function - switch the declarations of two variables.

void - use for printer functions because they don't `return` anything