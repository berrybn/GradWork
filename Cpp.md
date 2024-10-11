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
### Example - a table that prints the first 12 $N^2$ and $2^N$
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

### Example - raise 2 to a power n
```cpp
#include <iostream>

//function prototype
int raiseToPower(int n, int k);

//main program
int main(){
	int limit;
	std:cout<<"This program lists powers of two."<<endl;
	std::cout<<"Enter exponent limit: ";
	std::cin>>limit;
	for(int i = 0; i <= limit; i++)
	{std::cout<<"2 to the " << i << "=" << raiseToPower(2,i)<<endl;
	}
}

//function: raiseToPower - returns the integer n raise to 
//the kth power.
int raiseToPower(int n, int k){
	int result = 1;
	for (int i = 0; i <k; i++){
	result *=n;
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


const type = variable that will not be changed after initialization

unsigned = allow negative values

enum type 
`enum ListName {list};`



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
- switch - when we have to perform several decisions based on the situation
	- we have a *control expression* like an iterator or some equivalence statement
		- the program then executes a switch statement and it evaluates the control expression and compares it against the values c1, c2, and so forth, each of which must be a constant. 
	- If one of the constants matches the control expression, the statement in the associated *case* is executed
	- break at the end to signify the decision making is complete

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


## Classes
Classes allow programmers to create operators for abstract mathematical structures. 

## Inheritance
Suppose that you have been given the task of designing an object-oriented payroll
system for a company. You might begin by defining a general class called
`Employee` that encapsulates the information about an individual worker along with
methods that implement operations required for the payroll system. 
- These operations might include simple methods like: 
	- `getName()`, which returns the name of an employee, 
	- or `getPay()`, which calculates the pay for an employee based on data stored within each `Employee` object.
In many companies, however, employees fall into several different classes that are
similar in certain respects but different in others. 
- For example, a company might have hourly employees, commissioned employees, and salaried employees on the same payroll. 
	- In such companies, it might make sense to define sub-classes for each employee category as illustrated by the UML diagram in Figure 19-1.

base methods off what functionality you need
the class `Employee` exports methods like `getName()` for other classes to inherit
the functionality can be further specified between different employees, so even each subclass will need a `getPay()` method. 
- An hourly worker's pay will not be the same as a salary worker's pay, or a commissioned employee. 
for `getPay()` We will specify the method a at the `Employee` class level and then override that definition in each subclass

in our implementation we declare the getPay() method a *pure virtual method* as: 
`virtual double getPay()=0;`
meaning it has no definition in the base class and can therefore come only from a subclass -- which is what we need so we can specify different getPays for different types of employee

In many hierarchies, the base class provides a default definition, which is then overridden only in those subclasses that need to change it.

If you leave out the `virtual` keyword, the compiler determines which version of a method to call based on how the object is declared and not on how the object is constructed. 
- For example, even if you were to override the getName method in the SalariedEmployee subclasses, calling getName on a variable declared to be an Employee would call **the original version** of getName defined in the Employee class, even if you created that object as a SalariedEmployee. The new version of getName is used only on a value declared to be a SalariedEmployee.

the class header indicates the inheritance relationsihp by adding a colon, the keyword public and the parent class name after the child class. The child class automatically inherits the public methods of the parent class. 

since `getPay` is defined as a pure virtual method in the `Employee` class, we need to define it in each subclass we use. 

Each subclass definition must therefore inform the compiler that it is overriding the getPay method by including the following virtual prototype:
`virtual double getPay();`



# CLASS 3
the difference between getline and cin 
to read the entire line from the user use getline. cin will only work up to the whitespace

function overloading - two functions with the same name as long as they have different arguments

Assignment 1 
Write a program that prompts the user for their first name, last name, address, and phone number
Store the information 

**Write a procedure reverse that reverses the sequence of elements in a vector**

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


# COMPILE: g++ -o ./hello hello.cpp

# RUN: ./hello
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


C++ makes a true copy - if we intend to have a reference instead of a copy 

swap function - switch the declarations of two variables.

void - use for printer functions because they don't `return` anything


# Class 6

Strings
cin >> will only read up to a white space

getline to get the entire line

C++ Language Vs C++ Syntax
It's difficult to know the difference between what words are C++ and what words are custom for the programmer to use

do i have to use str every time i want to establish a string as a variable? like with vectors and vec?


# Class 7
Streams
iostream stringstream
std::ostream
interact with the stream using the >> operator

right justifiied persistent setting - until you turn it off it continues to work
setw(2) << i applies to i value (sets width for character)
setw(8)<< raiseToPower(2,i) applies to raiseToPower fxn (sets width for function output)

cin creates a command line prompt that allows the user to type until the y hit enter
each >> only reads until the next whitespace
everything after the first whitespace gets saved
stream buffer: `42_ab_4 \n`
int x; string y; int z;
cin>>x;
cin>>y;
cin>>z;

noskipws

file streams
ifstream and ofstream
declare a stream variable to refer to the file
open the file       `infile.open("filename.txt")`
transfer the data (read/write)
close the file       `infile.close()`

fstream can edit file in code
seekget `seekg(position)`
seekput `seekp(position)`

code whiles to where you don't need a break. Use conditions to END the loop

`infile.unget()` - pushes most recent character back into the input stream

`outfile.put(ch)` to write a char to file

# Class 8
headerfile for employee info code
```cpp
#include <string>

class Employee{
public:
Employee(std::string name);

std::string getName();
virtual double getPay()=0;

protected:
std::string emname;
};

class HourlyEmployee: public Employee{
public:
HourlyEmployee(std::string name, double wage, double hours);
double getPay();
private:
double wage;
double hours;
};

```
\
```cpp
#include "employee.h"
Employee::Employee(std::string name){

}

std::string Employee::getName(){
return name;
}

HourlyEmployee::HourlyEmployee(std::string name, double wage, double hours){

}
```

LAB - Inheritance

you can nest classes and structs within classes

implementations go in the .cpp file

Default constructor
takes no arguemtns
necessary if objects are going to be instantiated with no arguments

regular constructor

regular constructor with default arguments

default constructor - takes No arguments. 
Ball::vector::vector(){
x = 0.0;
y = 0.0; }

this - a pointer to the current instance of a class
implicitly included in all classes
only accessible to the memeber funcitons of the current class
this->velocity.x is equivalent to 

classes can inherit from other classes as long as they are children of the class

2 separate public and private declarations between the parent and child

constructor - compose(we will not use construct to mean tomake) 
C++ vocabulary!

empty constructor define in .h file

virtual - a function that can be overwritten by the child

```cpp
#include <iostream>

using namespace std;

class Animal;
public: virtual void speak(){
cout<<"Animal speaks"<<endl;
}
};

class Dog: public Animal{
public:
void speak() override {
cout<<"dog Barks""<<endl;
}
};

```

why use a pure virtual function?

virtual void speak(){
cout<<"animal noise"<<endl;
}

vector<Animal *> all Animals;
allAnimals.push_back(new Dog);

object slicing is why we use pointers (can point to any size) to ensure there is enough space to hold our stuff

sfml
create windows trigger sounds suited for 2d games
underrail

origin top right corner in pixels

game loop slide makes the assumption on frame rate - we will measure the time that it takes to draw a frame so we can use it to determine how much we want it to move instead of the frame rate itself. 

deltaTime = deltaclock.restart().asMilliseconds():
if(deltaTime<1)
draw frame

scale with time instead of frames
shape.move(.005*deltaTime, .005*deltaTime)

main function to drive lab code. dont edit. create the classes

uml diagram: 
screenSaver class - parent.
classic saver - child - doesn't change color
color saver - child of classic saver that does change color

custom saver is a child of screensaver that does whatever

lab5 scaffold

runtime polymorphism

we call an update function that will eb overwritten for every type to determine how your screensaver is working

move along velocity vector until hit wall
move along velocity vector until hit wall and also change color




screensaver class
{sf::CircleShape shape;

ScreenSaver();
ScreenSaver(float radius, sf::Vector2f, cVelocity, sf::Color color);

};

```cpp
#include <vector>
#include <iostream>

int Tens(int value)
{int ten = 10*value;
return ten;}

int main(){
std::vector<int> vec;
for(int i = 0; i <= 4; i++){
vec.push_back(Tens(i));
}
std::cout<<"The new vector is: "<<std::endl;
for (int i=0; i<=4; i++)
{std::cout<<vec[i]<<std::endl;}
return 0;
}

```

```cpp
#include <iostream>
#include <string>

std::string removeCharacters(std::string str, std::string remove)
{
for(char i:remove){
string.find(i)
}
}

int main(){

n = string.size("counterrevolutionaries);
				
for(int i=0;i<n;i++){
removeCharacters("counterrevloutionaries","aeiou");
}
std::cout<<new_string<<std::endl;
return 0;
}
```

```cpp
#include <iostream>
#include <string>

class Question{
private:

public:

}
int main(){
Book mybook
}
```

# Midterm

# Class 1
Recursion
Any solution technique in which large problems are solved by reducing them to smaller problems of the same form

if (test for simple case)
compute simple solution without using recursion
else 
	Break the problem down into subprobs of the same form solve each of the sub probs by calling this function recursively. Reassemble the subproblem solutions into a solution for the whole. 
Divide and conquer

Factorial 

```cpp
int fact(int n){
if (n ==0){
return 1;
}
else {
return n * fact(n-1)
}
}

```

computes the factorial from the bottom up (starting at fact(0)=1)

fibonacci sequence has too many recursive calls, without storing information, so when n gets big BAD, recurrence relation

Solution - STORE IT! In an array and reference the values when you need them

fib seq
int additive Sequence(int n, int t0, int t1)

int fib(int n)
	return additiveSequence()

we can pass information into a loop so that we only need to call it one time

str.length and substr are both going to loop through the code

even odd definition function

program an exit in your loops - figure out which parts will run infinitely if not controlled

microarchitecture

Induction for C++
Base case is often the key to figuring out how the induction works, is that the same here?






