[[C++]]
https://runestone.academy/ns/books/published/cpp4python/index.html
https://learn.microsoft.com/en-us/cpp/cpp/declarations-and-definitions-cpp?view=msvc-170
[[C_for_Engineers_and_Scientists.pdf]]
https://cplusplus.com/reference/string/string/getline/
https://www.learncpp.com/cpp-tutorial/basic-file-io/
https://www.cprogramming.com/tutorial/lesson12.html
#KhojSays 
# 0 - Preliminaries and Vocabulary
**Declare** - establishing the existence of various entities such as variables, functions, types and namespaces. Of the form: `int variableName` or `double Average()` or `using namespace std` or `int main()`
- Each of these must be declared before they can be used. 
- specifies a unique name for the item being declared
- specifies the data type for the item being declared - `int`, `float`, `std::vector`, etc.
- the name that is introduced by a declaration is valid only within the **scope** where the declaration occurs - either locally or globally 
	- declared inside the main: **local**
	- declared outside the main: **global**
- a function can be *forward declared* -- that is declared before definition with a **function prototype**.

**Initialize** - gives the declared an initial set value. We can initialize an integer type variable with: `int variableName = 500`. 
#PossibleError can occur if we have declared a variable of a specific type and initialize it to some other type. Consider the following code:
```cpp
#include <iostream>

int main(){
int myNumber = "Hello";
std::cout<<myNumber<<std::endl;
return 0;}
```
Which throws the error: `file0.cpp:4:16: error: invalid conversion from 'const char*' to 'int' [-fpermissive]`

**Define** - provides the compiler with all the information it needs to generate machine code when the entity is use later in the program. 
- Similar to *initialization* and *declaration* because both occur when we "define" an entity, however, we must also define a function or class, which would require more than just setting the initial value. 
	- The declaration CAN also be the definition - `std::string myNumber = "Hello"`

**Arguments** - values that are passed to the function, within the calling function

**Selection Statements** - (`if/else` and `switch`)provide a means to conditionally execute sections of code
**Iteration Statements** - (`while`, `for`, `do`)provide a means to iterate until the loop reaches the termination value, or is ended with the `break` command. 
1. `while (expression is true)` 
	- evaluated at the beginning of the loop, with no increments
2. `for (int i = 0; i <= {some upper bound}; i++ {increment})` 
	- evaluated at the beginning of the loop, that takes incremental values

**class** - a class encapsulates data for the object (known as *attributes* or *member variables*) and methods to operate on that data (*member functions*)

**methods** -  a function that operates within a specific scope within the code. 

**object** - instance of a class. When an object is created, the class's blueprint is used to allocate memory for the object and initialize its attributes.
#KhojSays 
```cpp
#include <iostream>
using namespace std;

// Define a class named 'Car'
class Car {
  public:
    string brand;  // Attribute (string variable)
    string model;  // Attribute (string variable)
    int year;      // Attribute (int variable)
    
    // Method that displays information about the car
    void displayInfo() {
        cout << "Brand: " << brand << ", Model: " << model << ", Year: " << year << endl;
    }
};

int main() {
    // Create an object of Car
    Car car1;
    car1.brand = "Toyota";
    car1.model = "Corolla";
    car1.year = 2020;

    // Create another object of Car
    Car car2;
    car2.brand = "Honda";
    car2.model = "Civic";
    car2.year = 2022;

    // Call the method on car1
    car1.displayInfo();
    
    // Call the method on car2
    car2.displayInfo();

    return 0;
}
```
# 1 - Atomic Data Types
**Data Types**
integer - `int`
floating point - `float`
double precision floating point - `double`
boolean - `bool`
character - `char`
special type that holds the memory location - `pointer`
enumerated type a user defined type that defines a set of named constants, enumerators - `enum`
- #KhojSays  can be used when you need take one variable out of a set of possible values. Compass directions or days of the week
variable that is not changed - `const datatype varName`
- we CAN create custom types, they just must be defined

## Arithmetic Operations: +, -, * , and /
The standard operators are the same in C++ with the exception of powers and integer division. In C++, dividing $3/2$ will result in 1 instead of 1.5 because the compiler removes the fractional portion of the answer. In addition to division, raising numbers to an exponent is used with `pow(base,exp)` rather than base ** exp or base^exp.   

There are mathematical functions that exist within the `#include <cmath>` library
[[cmath ref]]: (some common functions)
`abs(x)` 	Returns the absolute value of x
`ceil(x)` 	Returns the value of x rounded up to its nearest integer
`exp(x)` 	Returns the value of $e^x$
`exp2(x)` 	Returns the value of $2^x$
`floor(x)` 	Returns the value of x rounded down to its nearest integer
`log(x)` 	Returns the natural logarithm of x
`log10(x)` 	Returns the base 10 logarithm of x
`pow(x, y)` 	Returns the value of x to the power of y
`sqrt(x)` 	Returns the square root of x
`sqrt(x)` 	Returns the square root of x
`cos(x)` 	Returns the cosine of x (x is in radians)
`sin(x)` 	Returns the sine of x (x is in radians)
`tan(x)` 	Returns the tangent of x (x is in radians)

## Boolean Data Types: 
When a decision or comparison is needed (validation - isTrue)
greater than `>`, greater than or equal to `>=`
less than `<`, less than or equal to `<=`
equal `==`, not equal `!=`
logical and `&&`, logical or `||`, logical not `!`

Boolean types return true (1) or false (0) for each expression

**Boolean Example:** 
```cpp
int main(){

//declare theSum variable as int = 4, print theSum.
int theSum = 4;
std::cout<<theSum<<endl;

//re-define theSum as theSum+1, print theSum.
theSum = theSum+1;
std::cout<<theSum<<endl;

//declare theBool variable as boolean = true value, print theBool.
bool theBool = true;
std::cout<<theBool<<endl;

//re-define theBool as =4, =
theBool = 4;
std::cout<<theBool<<endl;

return 0;
}
```
Here, the output is as follows: 4, 5, 1, and 1. 
- This is because for boolean statements false == 0 and true = !false so anything that is not zero can be converted to a Boolean is not false, thus it must be true. 
- Boolean statements deal in 1's and 0's. So an entry of `theBool = 0`, will result in a 0 output, any other value however will hold true, because they are NOT 0. 

## Characters and String types:
In C++,  we represent characters with `'char'` single quotes and strings `"string"` with double quotes
We must have `#include <string>` to use strings and the syntax `std::string var = "string"`.

We can just declare a variable or function a `char`
## Enums
An `enum` is a special type that represents a group of constants (unchangeable values)

```cpp
enum Level{
LOW = 25,
MEDIUM = 50,
HIGH=75
};

enum Level myVar;  //keyword = Level, variable = myVar

int main(){
enum LEvel myVar = MEDIUM;
//set myVar to MEDIUM

std::cout<<myVar<<endl;
//print myVar

return 0;
}
```

By default, the first item `LOW` has the value 0, the second `MEDIUM` has the value 1, and etc.

Because we have set `myVar` = MEDIUM, when we go to print `myVar` it will output the default value for the second position, 1. But we have set each  level to a specific value, so MEDIUM will output 50. 

- Enums are used to give names to constants, which makes the code easier to read and maintain
- Use enums when you have values that you know arent going to change, like months, days, colors, deck of cards
# 2 - Control Structures
Algorithms require two important control structures: **iteration** and **selection**. 
## if (condition) {statements}
technically a function that returns true or false

`if - else` (condition){statements}
```cpp
#include <iostream>
#include <string>

int PasswordValidate(std::string entry)
{std::string password = "OpenSesame";
 if (entry == password)
	return 1;
else return 2;
}

int main()
{std::string pwd;
std::cout<<"enter your password:"<<std::endl;
std::cin>>pwd;

if (PasswordValidate(pwd)==1)
std::cout<<"welcome!"<<std::endl;
else
std::cout<<"Wrong Password!"<<std::endl;

return 0;

}
```

`elif`
else if, to continue to decide through different cases

## switch
A statement that takes and checks the validity of the case against the code. cases must be integer-based or enumerated constant

 **Switch Example:**
```cpp
#include <iostream>

int main(){
	int grade = 85;

	int tempgrade = grade /10; //since switch deals in integer values, we declare tempgrade as an int and use the cases to decide each grade
	
	switch(tempgrade){
	case 10:
	case 9:
		std::cout<<"grade = A"<< endl;
		break;
	case 8:
		std::cout<<"grade = B"<< endl; //tempgrade = 8.5, will output 8 as integer
		break;
	case 7:
		std::cout<<"grade = C"<< endl;
		break;	
	case 6:
		std::cout<<"grade = D"<< endl;
		break;
	default:
		std::cout<<"grade = F" <<endl;
	}
return 0;
}
```

## while and for loops
To repeat a block of code a `while` or `for` loop is best

A `while` loop repeats a body of code as long as a condition holds true
They have the following structure:

```
initialize some counter
while (counter boolean_statement value)
{statement;
increment counter either up++ or down--;
}
```

**while example:** 
```cpp
#include <iostream>

int main(){
	int counter = 0;
	while(counter<=5)
	{std::cout<<"Hello World"<<endl;
	counter = counter +1;}
return 0;
}
```
Output for this bit of code will be "Hello World", 5 times. 

### For Loops - floops
A `for` loop allows to iterate across a range of values and the loop will be executed a specific number of times.
They have the following structure:

for(initialize iterator type; duration of loop; increment iterator)

**for example:**
```cpp
#include <iostream>

int main(){
	for(int i = 0; i < 5; i++)
	{std::cout<<i*i<<" "<<endl;}
return 0;
}
```

# 3 - Functions
Functions are of the format: 
```
type name(parameters){
...body...
return expression; }
```

When creating a function, you must be concerned with not only constructing the function itself, but also with how it will interact with other functions, i.e. the `main()`. *Function interaction* primarily involves:
1. passing data to a function correctly when it's called  
2. returning values from a function when it ceases operation. 
## Calling a function:
- A function is a block of code that performs some operation. 
- A function CAN define input parameters that enable function callers to pass arguments into the function. This is not a requirement. For Example: `int Avg(int score, int class_size)`
- A function CAN return a value as output `return average` or `return expression`
- The values that are passed to the function are the `arguments` whose types must be compatible with the parameter data types that have been declared
- Functions need to perform a **single well-defined task**
- **member functions** are functions that are defined at class scope, but they can also be defined at the namespace scope (free functions)

To **declare** a function, we need
1. return type - data type of the function that we initially set in the definition. It applies to the return value.
2. function name 
3. parameter list (optional)
		return type ->`float Avg()`<- function name(parameter list)
4. keywords (optional)

To **call** a function, we need:
1. the function name
2. variables to be passed to the function. 
	1. These should be declared in the same scope in which the function is called. 
```cpp
#include <iostream>

float Avg(float score_sum, int class_size)
{
float average;
average = score_sum/class_size;
return average;
}

int main(){
float scores;
std::cout<<"enter the sum of the class scores: "<<std::endl;
std::cin>>scores;
std::cout<<"The class average is: "<<Avg(scores,20)<<std::endl;
return 0;
}
```
Here we prompt the user to input the class sum, which we have declared as `float scores`, we call the function `Avg()` and we **pass by value** to the function the score and an integer that will be used as the `class_size` variable within the function -> `Avg(scores, 20)`

## Function Anatomy:
A **parameter** is a placeholder for one of the arguments supplied in the function call and acts in most respects like a local variable. *"function variable"*
- each parameter is initialized automatically to hold the value of the corresponding argument in the function call. 
	- if a function takes no parameters, no entry in ()
	- no more than 5 parameters
- **return value/type** - when we declare a function type, that is the value type that will return/ output with the function call. 
	- *"what kind of data type will the function give back when called?"*
- the **function body** performs the operations, and returns some value;

```cpp
#include <iostream>
//define fxn timesTwo that takes parameter int num
int timesTwo(int num){ 
	return num*2; //bc int type fxn, returns int
}
int main(){ //call the fxn, pass a value of type
	std::cout<<timesTwo(5)<<std::endl;
return 0;
}
```

Here we have **defined** the function `timesTwo(int num)` that accepts integer type variable number. 
- Because we have declared the function return type as `int times Two`,  when the function is called in the main, it will return a value of integer type using the return expression: `num*2`. 
- The value that is passed to the function will be declared `int num` and the function will perform the calculation with the `num` variable and return the int  to the main function. 
	- In the main, we pass by value the integer 5 to the `timesTwo(5)` function and the output will be 10 ($2*5=10$)

The **function prototype** is comprised of:
1. return type 
2. function name, and parameters. It can be used to initially declare function for later use in the code. 
```cpp
#include <iostream>
int timesTwo(int num);  //this is a function prototype

int main(){
std::cout<<timesTwo(5)<<std::endl;
return 0;
}

int timesTwo(int num){   //here is the function definition
return num*2;
}
```
### void
Use the "type" `void` when the function does not return any value to the compiler.
- use for printers to output to the screen, without returning anything to the main
```cpp
#include <iostream>

int Summer(int addend){

int x = addend + 100;
return x;
}

void printSum(int x)
{
std::cout<<"the sum is: "<<x<<std::endl;
}

int main(){

int addend;

std::cout<<"enter a number to sum with 100"<<std::endl;
std::cin>>addend;

Summer(addend);
printSum(Summer(addend));

return 0;
}
```

Functions follow the same format as the mathematical $f(x)$. In the body we can have statements, but the importance here is that the body acts as the "function machine" and the `return` statement acts as the true "output" for the function. 

```cpp
#include <iostream>

void timesTwoVoid(int num){
std::cout<<num*2<<endl; //here, 
}

int main(){

timesTwoVoid(5);  //pass 5 to the function timesTwoVoid(int num)

return 0;
}
```
output will also be 10, but here we call the function in the main, and in our actual function we declare it `void` which means it doesn't return anything, but here is where we will display the product of `num*2`.
## Function Example
**Square Root Function - implementation of Newton's Method:**
```cpp
#include <iostream>

double squareRoot(double n){
	double root = n /2;
	for(int i = 0; i < 20; i++){
	root = 0.5*(root+(n/root));
	}
return root;
}

int main(){
	std::cout<<squareRoot(9)<<endl;
	st::cout<<squareRoot(4563)<<endl;
return 0;
}
```
Newton's Method for approximating square roots: $\text{new guess} = \dfrac{1}{2} \cdot \bigg(\text{old guess}+\dfrac{n}{\text{old guess}}\bigg)$, with an initial guess of $\dfrac{n}{2}$. In the main we pass by value the integers 9 and 4563 to the function `squareRoot(double n)` and the output gives the square roots of 9 and 4563, 3 and approximately 67.55 respectively. 

## Function Recursion
```cpp
#include <iostream>

int countdown(int n){
//base case
if (n==0){
std::cout<<"0...Blastoff"<<std::endl;
return 0;
}
//recursive case
std::cout<<n<<std::endl;

return countdown(n-1); //function called based on n times

}
int main(){

countdown(5);
return 0;}
```
## 3.2 - Passing by Value vs Passing by Reference
Calling a function involves ***copying the contents of the arguments into the memory locations of the corresponding formal parameters***. Whenever you pass a simple variable from one function to another, the function gets a copy of the calling value. 
- Assigning a new value to the parameter as part of the function changes the local copy but has no effect on the calling argument. 
- Consider the following code:
```cpp
void functionExample(int inputVar){
	int nextVar = inputVar * 2;
	inputVar = 4;
	std::cout<<nextVar<<" "<<inputVar<<endl;
}

void callingFunction(){
	int myVar = 10;

	functionExample(myVar);
	std::cout<<"myVar ="<<myVar;
}
```
- Here, when `callingFunction` executes, it calls `functionExample` and **passes by value** `myVar`, which has been set to 10. 
- In `functionExample`, the value 10 is copied from `myVar` to the formal parameter `inputVar`, so the value of `nextVar` will be $2*10=20$. 
- The next statement changes the contents of `inputVar` to 4 so the output statement gives: 20 4. 
- Also, since `myVar` still has the value 10, the output statement in `callingFunction` gives `myVar = 10`

When we want a function to return more than one value to the calling program, we will use **pass by reference**. 

 **Pass By Reference Example:**
```cpp
#include <iostream>

void swap_values(int &variable1, int &variable2)
//here we reference variable1 and variable2, which makes copies of them in the memory, so that we can connect the values of these function parameters to the variables that are declared in the main
{
	int temp; 
//here we need a dummy variable 'int temp' to hold one of the variables to swap. If I want to swap two things, I need a third thing, for storage, so one of the target items can be empty, to receive whatever is in the other target item -- effectively swapping them. 

	temp = variable1; 
	// here temp is empty, and we put variable1 in for storage
	variable1 = variable2; 
	// here we overwrite the value in variable1 with variable 2
	variable2 = temp;
	// here we overwrite the value in variable2 with temp, which is variable1
}

int main(){
	int first_num, second_num;
	first_num = 7;
	second_num = 8;

	std::cout << "Two numbers before swap function: 1) " << first_num << " 2) " << second_num << endl;
    swap_values(first_num, second_num);
    std::cout << "The numbers after swap function: 1) " << first_num << " 2) " << second_num;

    return 0;
}
```
Here the output will show 1) 7  and 2) 8 and then swap them 1) 8 and 2) 7 . Without the reference operator `&`, the values `first_num` and `second_num` are passed by value to the function, and they will overwrite whatever values are placed in the variables there.   

## 3.3 - References and Pointers
We use a reference to create an empty version of the variable to be used as needed, without changing or doing math with the original information. 

**Passing by value vs Passing by reference**
```cpp
void func1(int var1, int var2)
{
	int temp
	
	temp = var1 
	//temp is given the value of var1 bc it is empty
	var1=var2 
	//var2 will be overwritten with what is in var1
	var2=temp 
	//because temp will be overwritten with what is in var2
}

int main(){
int num1 = 2;
int num2 = 3;

func1(num1, num2);
}
```
output will still be 2, 3 because we pass by value, and var1, var2 are overwritten bc they are copies of the original variables 

Passing by reference allows for the creation of direct memory references aka "container variables" that we can empty and fill as we need with the original variable values

Arrays as Parameters in Functions:
array parameters are used to pass an array of values to a function as a parameter

**A function to give the average number of hours worked:**
```cpp
double average(int list[], int length){
	int count;
	//declare iterator type, integer
	for(count = 0; count < lenghth; count++){
		total += double(list[count]);
	//tally each hour by counting for each hour up to the length of the shift, store in array list and 
	}
	return (total/length);
}
```

## 3.4 - Function Overloading
Creating multiple functions with identical names but different implementations. Allows for: 
1. Consistency in the way functions are named across code
2. Functions that do similar tasks will differ based on parameters instead of by name
3. Fulfilling multiple tasks depending upon parameters
**Function overload example:**
```cpp
#include <iostream>

double Area(int s){ //to find area of a square
double Sarea = s*s;
return Sarea;
}

double Area(int l, int w){ //to find area of a rectangle
double Rarea = l*w;
return Rarea;
}

int main(){
std::cout<<"The square area is: "<<Area(3)<<std::endl;
std::cout<<"The rectangle area is: "<<Area(3,4)<<std::endl;

return 0;
}
```
### Possible Function Errors:
1. If you declare two parameters for the function to take, but only pass one, the compiler will throw the error: `"too few arguments."`
2. Order of declaration matters! Use prototypes if the main comes before a function declaration.
3. data type matters! If you declare a parameter an int and pass a float it will throw the error: `ambiguous`
4. segmentation fault - stack overflow. 
#### Functions Problem:
"methinks it is like a weasel"
word1 = methinks, count = 8 <- would size_t work here to give length of each string?
word2 = it, count = 2
word3 = is, count= 2
word4 = like, count = 4
word5 = a, count = 1
word6 = weasel, count = 6

How long will it take for a C++ function to generate this sentence?
Write a function that generates a string that is 28 characters long by choosing random letters from the alphabet, plus the spaces. 
- this is how many total characters that are in our target phrase "methinks it is like a weasel"

Write another function that will score each generated string by comparing the randomly generate string to the goal. 


Write a third function that will repeatedly call generate function and score functions and if 100% of the letters are correct, done. If not correct, generate a new string. It should print the best string and its score every 1000 tries. 

`size_t` declaration type used to represent the size of objects

```cpp
#include <iostream>
#include <random>
#include <string>

std::string stringGenerator(){

}


```


See if you can improve upon the program in the self check by keeping letters that are correct and only modifying one character in the best string so far. This is a type of algorithm in the class of ‘hill climbing’ algorithms, that is we only keep the result if it is better than the previous one.


## 3.5 -  Pointer types:
**A pointer is a variable that stores the memory address** and can be used to indirectly access data stored at that memory location

- We know that variables in a computer program are used to label data with a descriptive identifier so that the data can be accessed and used by that computer program - that's the memory location
- In C++, the value of each variable is stored directly in memory without the need for either a reference or an object -- this makes access faster, but it is one of the reasons we need to declare each variable because different types take different amounts of memory
- **What scenarios would using a pointer be appropriate?**
	- #KhojSays We use pointers when:
		- we need dynamic memory allocation -- so the size can change at run-time
		- implementing data structures bc they allow elements to be linked in various ways to form these structures
		- passing large structures to a function, because passing by value can be inefficient due to the copying of data. The function can access and manipulate the original data without the overhead of copying
		- passing a function as an argument to another function
		- iterating over array elements
		- low level programming - direct memory access is required. used for interfacing with hardware, manipulating memory blocks, and implementing optimized system routines
		- Polymorphism -- when you have functions of the same name that do different things
			- occurs when we have many classes that are related by inheritance
			- 

`int varN = 100;` stores the value 100 in the memory slot for `varN`

when declaring a pointer that will "point" to a memory address of some data type, we use the following syntax: `variableType *identifier`. For example: `int *ptrx; ` declares a pointer `ptrx` to an integer

We need to give the pointer the address of where the value is going to be stored -- one way to do this is to have a pointer refer to another variable by using the **"address-of" operator `&`**. Which gives the following syntax: `variableType *ptrN = &varN`. This gives a variable pointing to the address of `varN`. In this way `varN` and `*ptrN` refer to the same value in code. This is called *de-referencing the pointer*.

**Pointer Example:** 
```cpp
#include <iostream>

int main(){
	int varN = 9;
	int *ptrN = &varN;
	std::cout<<"varN value"<<varN<<std::endl;
	std::cout<<"varN location"<<ptrN<<std::endl;
	std::cout<<"deref ptrN:"<<*ptrN<<std::endl;

return 0;
}
```

- Will output the value of `varN` = 9
- The *location in memory* of `varN`, given by the expression `int *ptrN=&varN` = 0x7fffa7e0980c
- dereferenced pointer with `*ptrN`, which will return the same value as `varN` initially, = 9. 

we also have `nullptr` which points to nothing -- used for conditions and logical operations. 

### Pointers and References
Since a pointer is a variable that stores the memory address (what is stored in the `&variable`) as its value, we can utilize that behavior to avoid memory issues
```cpp
#include <iostream>
#include <string>

int main(){
std::string food = "Pizza";
std::string* ptr = &food;
//create a pointer to a string that will hold the ref for "food", the 
//memory address

std::cout<<food<<std::endl;
//will display "Pizza"

std::cout<<&food<<std::endl;
//will display memory address for "food" variable

std::cout<<ptr<<std::endl;
//will display memory address for "food" variable

std::cout<<*ptr<<std::endl;
//dereferenced pointer, will display "Pizza"
*ptr = "Hamburger";
//change the value of what pointer is holding

std::cout<<*ptr<<std::endl;
//dereferenced pointer, will display "Hamburger"

return 0;
}
```


## 3.6 - Structs
A way to group several variables into one place - each variable is called a **member**
A way to bundle variables -- like a class without the behavior, only the data

We need to keep in mind that defining the struct introduces a new type and does not in itself declare any variables. Once you have the definition, you can use the type name to declare variables, just as you would with any other type. 

**==kind of like custom types?==**

To create a struct, we use the keyword `struct VariableGroupName`
```cpp
struct Student{
std::string name;
std::string state;
int age;
//these are called fields, they hold components for the struct
}
```
After the initial declaration, we establish a structure name that behaves as a data type `StructName structVar`, and the corresponding variable `structVar` for that type. In order to access field members to assign values, we use the `.` operator with the following syntax: `structVar.fieldMem`
```cpp
Student s;
//local variable declaration for the compiler to reserve space in the stack frame for a variable of type Student named s
s.name = "Sarah";
s.state = "CA";
s.age = 21;
//
```

The following example creates a struct to hold a car's brand name, model name and year. Then the main passes the values for each field to the struct. In addition, we establish two structure variables `mycar1` and `mycar2` so that we can print the information for two different variables using the same structure `struct car`

**struct example:**
```cpp
struct car{
string brand;
string model;
int year;
}

int main(){
car mycar1;

mycar1.brand = "BMW";
mycar1.model = "X5";
mycar1.year = 1999;

car mycar2;

mycar2.brand = "Honda";
mycar2.model = "Accord";
mycar2.year = 1990;
}

std::cout<<mycar1.brand<<" "<<mycar1.model<<" "<<mycar1.year<<std::endl;
std::cout<<mycar2.brand<<" "<<mycar2.model<<" "<<mycar2.year<<std::endl;
```

# 4 - Collection Data types
Collections and Arrays

`collection` data type is a grouping of some number of other data items that have some shared significance or need to be operated upon together. 
- arrays, vectors, strings, sets, and hash tables
## Arrays
An **array** is a data structure consisting of an ordered collection of data elements, of identical type, in which each element can be identified by an **array index**, i
- *statically allocated* means the array size is fixed at compile time
	- typically used when speed is essential or hardware constraints exist
- *dynamically allocated* means pointers are used in the allocation process so the size can change at run-time
	- we could use a `vector` data structure when more flexibility is required
For a compiled language, the compiler checks the types before the program runs (compile time)

We can declare the type, the size and even initialize the array at compile time (during the run)

```cpp
double darray[4];
int iarray[10];
char arr2[3000];
```

```cpp
int arr[] = {1, 2, 3, 4};  // This is size 4.
char arr2[] = {'a', 'b', 'c'}; // This is size 3.
string arr3[] = {"this", "is", "an", "array"}; // This is size 4.
```

Note that an array with a single element is not the same type as the **atomic** type, so the following are not the same.
```cpp
double darray[] = {1.2};  // must use index to access value
double ddouble = 1.2;     // cannot use index to access value
```

we can change the value of a specific element in an array with `myarray[0]="Honda"`. This will change the first entry in the array of car brands to "Honda".

**Array example - note style of output**
```cpp
#include <iostream>
using namespace std;

int main(){
    int myarray[] = {2,4,6,8};
    for (int i=0; i<4; i++){
        cout << myarray[i] << endl;
    }
    return 0;
}
```
Output will be:
2
4
6
8
### Looping through the array
You can loop through the array elements with a for loop -- floop!

Output all cars in the array `cars[5]`
```cpp
std::string cars[5] = {"Volvo", "BMW", "Ford", "Mazda", "Tesla"};
for (int i = 0; i < 5; i++)
{std::cout<<cars[i]<<"\n";
}
```
Will output the car brands in a vertical list:
Volvo
BMW
Ford
Mazda
Tesla

outputs each element with its value
```cpp
std::string cars[5]={"Volvo", "BMW", "Ford", "Mazda", "Tesla"};
for (int i = 0; i < 5; i ++){
std::cout<<i<<"="<<cars[i]<<"\n";
}

//OR can also use a for-each syntax:
for (int i:cars){
std::cout<<i<<"="<<cars[i]<<"\n";
}

```
Outputs the vertical list:
0 = Volvo  
1 = BMW  
2 = Ford  
3 = Mazda  
4 = Tesla

looping through an array of cars using a for-each loop:
```cpp
std::string cars[5] = {"Volvo", "BMW", "Ford", "Mazda", "Tesla"};
for(std::string car : cars){
std::cout<<car<<std::endl;
}
```

CAN declare array elements outside of the array: `array[i]= value`. this approach only works if we have specified array size. `array[size]`.

We use `sizeof(array)` to determine the size of the type in bytes. We can use that to return the number of elements in the array or the size of an individual element in the array with:
```cpp
int myNumbers[5] = {10, 20, 30, 40, 50};  
int getArrayLength = sizeof(myNumbers) / sizeof(int);  //sizeof(myNumbers[0])
std::cout << getArrayLength;
```

Multi-Dimensional Arrays

#### **how to determine the element index in an array?**
#### #KhojSays 
To determine the index of an element in an array in C++, you can use the `std::find` function from the `<algorithm>` library, combined with `std::distance` to calculate the index. Here's a concise example to illustrate this method:

```cpp
#include <iostream>
#include <algorithm> // For std::find
#include <iterator>  // For std::distance

int main() {
    int arr[] = {4, 1, 3, 2, 6}; // Example array
    int target = 3; // Element to find
    auto it = std::find(std::begin(arr), std::end(arr), target); // Find the iterator to the target

    if (it != std::end(arr)) {
        // Calculate the index
        int index = std::distance(std::begin(arr), it);
        std::cout << "Element found at index: " << index << std::endl;
    } else {
        std::cout << "Element not found." << std::endl;
    }

    return 0;
}
```

This code snippet searches for the element `3` in the array `arr` and prints its index. The `std::find` function returns an iterator to the first occurrence of the target element. If the element is not found, it returns an iterator to the end of the array. The `std::distance` function then calculates the distance between the beginning of the array and the iterator returned by `std::find`, effectively giving you the index of the element.

For a more detailed explanation and additional methods, you can refer to the comprehensive guide on [GeeksforGeeks](https://www.geeksforgeeks.org/find-the-index-of-an-element-in-an-array-in-cpp/), which was updated on March 18, 2024. This guide covers the use of the `find()` function for locating the index of a specific element within an array in C++, providing practical examples and a C++ program to demonstrate the concept.

## Vectors
Vectors use dynamically allocated arrays to store elements so they can change size
contiguous storage locations, elements can be accessed and traversed, and access randomly using indexes.

Vectors are a class -- `#include <vector>`
**Methods:**
`myvector[i]` = access an element of vector "`myvector`" at index i
`myvector[i]=value` = assign value to an element at index i
`myvector.push_back(item)` = appends item to the end of the vector list
`myvector.pop_back()` = deletes the last item from the end of the vector list
`myvector.insert(i, item)` = inserts item at index i
`myvector.erase(i)` = erases an element from index i
`myvector.size()` = returns the actual size used by elements
`myvector.capacity()` = returns the size of allocated storage capacity
`myvector.reserve(amount)` = request a change in capacity to amount

A common programming task is to grow a vector using `push_back()` method to append to the vector
```cpp
// A vector with 3 elements  
vector<string> cars = {"Volvo", "BMW", "Ford"};  
  
// Adding another element to the vector  
cars.push_back("Tesla");
```

## Strings
`string[i]` = access a character of  `string` at index i
`string[i]=value` = change value of character at index i
`string1 + string 2` = concatenate strings
`string.append(string_var)` = appends a string to the end of the string 
`string.push_back(char)` = appends a character to the end of the string
`string.pop_back()` = deletes the last character from the end of the string
`string.insert(i, string)` = inserts a string at index i
`string.erase(i,j)` = erases j characters beginning at index i
`string.size()` = returns the size of the string
`string.find(item)` = returns the index of the first occurrence of item

char - 'a'
string - "a"

We can concatenate two strings with the `+` operator or using `.append(variable)`:
```cpp
string firstName = "John ";  
string lastName = "Doe";  
string fullName = firstName + lastName;  
//OR
string fullname = firstName.append(lastName);
std::cout << fullName;
```

## Hash tables, maps
A hash table is a collection of associated pairs of items where each pair consists of a key and a value. Hash tables are often called maps bc the associated function maps the key to the value. 
`#include <unordered_map>`

```cpp
#include <iostream>
#include <unordered_map>
#include <string>

int main(){

std::unordered_map<string, string> spnumbers;
spnumbers = {{"one", "uno"}, {"two","dos"}};

spnumbers["three"] = "tres";
spnumbers["four"] = "cuatro";

std::cout<<"one is";
std::cout<<spnumbers["one"]<<std::endl;

cout<<spnumbers.size()<<std::endl;

return 0;
}
```

Looping through an unordered map doesn't work sequentially because they are organized by the location given by the hash function. Iterators of an unordered map are then implemented using pointers to point to elements of the value type: 
```cpp
#include <iostream>
#include <unordered_map>
#include <string>

int main(){
unordered_map<std::string, std::string> spnumbers;

spnumbers = {{"one","uno"},{"two","dos"},{"three","tres"},{"four","cuatro"}}

for(auto i=spnumbers.begin(); i!=spnumbers.end(); i++){
std::cout<<i->first<<":";
std::cout<<i->second<<std::endl;
}

return 0;
}
```

`mymap[k]` = returns the value associate with k, otherwise throws error
`mymap.count(key)` = returns true if key is in `mymap`, false otherwise
`mymap.erase(key)` = removes the entry from  `mymap`
`mymap.begin()` = an iterator to the first element in `mymap`
`mymap.end()` = an iterator pointing to past the end of `mymap`

Unordered Sets
An unordered_set is an unordered collection of zero or more unique data values of a particular type



# 5 - Header Files/Custom Libraries
## Interfaces and Implementation
When you define a library, you need to give the **interface** - which provides the information clients need to use the library but leaves out the details about how the lib works. The `.h` file the **header file**

you also need to give the **implementation** - which specifies the underlying details. The `.cpp` file.  

**what's the difference between a header file and a function protoytpe?**
#KhojSays The primary purpose of a function prototype is to ensure that a function is called correctly, in terms of both the number and types of arguments. Header files serve a broader purpose, including sharing declarations between files, reducing code duplication, and organizing code logically.







# 6 - Error Handling
The use of `std::cerr` for error messages is a common practice in C++ programming, as it ensures that the error output is immediately visible and can be separated from the standard output if needed, such as redirecting it to a different file or device.

# RECIPES

#### Basics
- [ ] Write a program that prompts the user for their first name, last name, address, and phone number, store the information in a struct and display it neatly
```cpp
#include <iostream>
#include <string>

int main(){
std::string FName;
std::string LName;
std::string address;
std::string phone;

std::cout<<"Enter your First Name:"<<std::endl;
std::getline(std::cin, FName);
std::cout<<"you entered:"<<FName<<std::endl;

std::cout<<"Enter your Last Name:"<<std::endl;
std::getline(std::cin, LName);
std::cout<<"you entered:"<<LName<<std::endl;

std::cout<<"Enter your address:"<<std::endl;
std::getline(std::cin, address);
std::cout<<"you entered:"<<address<<std::endl;

std::cout<<"Enter your phone number:"<<std::endl;
std::getline(std::cin, phone);
std::cout<<"you entered:"<<phone<<std::endl;

return 0;
}
```

#### Functions

#### Structs

#### Arrays

#### Vectors

#### Maps

#### References

#### Pointers

#### Custom Libraries

#### Classes



2. Reverse the sequence of elements in an **array:**
```cpp
#include <iostream>

using namespace std;

// Reverse function definition
void reverse(int arr[], int size)
{
    // Start the for loop
    for (int i = 0; i < size / 2; i++) 
    //<- size/2 is for positioning. For an array, we only need to loop through half of it to switch positions
    {  // For reversing the elements
        int temp = arr[i];
        //create a temp var to hold each element through the floop
        arr[i] = arr[size - i - 1];
        //position the 1st elements at the back 
        arr[size - i - 1] = temp;
        //send the value to temp var to be assigned to arr[i]
    }
}

// Start the main() function
int main()
{
    int n = 9;
    int arr[n] = {2, 5, 6, 4, 7, 8, 3, 6, 4};

    // Calling the reverse function
    reverse(arr, n);
    //pass by value int array, arr and int size, n

    // Print the reversed array
    cout << "The reverse of the array is ";
    for (int i = 0; i < n; i++)
    {
	    cout << arr[i] << " ";
	    //for each new arr[i] set from reverse()
    }
	    cout << endl;
    return 0;
} // end the main function
```
3. 