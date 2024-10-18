CS300/CS500
Advanced Object-Oriented Programming with C++
# Lecture 1 - Types, Function Overload, Struct
- [x] **Write a program that prompts the user for their first name, last name, address, and phone number** ✅ 2024-10-13
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
- [x] Experiment with `cin` and `getline`. What's the difference?
	- with `cin`, you can only read up to the white space, only one whole word entry, whereas with `getline`, you can read the whole string, BUT `getline` needs an output statement directly after it to work properly.
	- I like `getline` better because it makes it more streamlined ... more lines of code though :( 
- [x] Experiment with std::endl
	- `std::endl` makes sure each entry is on a separate line. like hitting enter in a word processor
- [x] **Store the information in a struct** ✅ 2024-09-20
```cpp
struct Info{
std::string FName;
std::string LName;
std::string address;
std::string phone;
}

int main(){

Info f;

std::cout<<"Enter your First Name:"<<std::endl;
std::getline(std::cin, f.FName);

std::cout<<"Enter your Last Name:"<<std::endl;
std::getline(std::cin, f.LName);

std::cout<<"Enter your address:"<<std::endl;
std::getline(std::cin, f.address);

std::cout<<"Enter your phone number:"<<std::endl;
std::getline(std::cin, f.phone);

return 0;
}
```
- [x] **Write a function that displays the struct's information neatly** ✅ 2024-09-20
```cpp
#include <string>
#include <iostream>

struct Info{
std::string FName;
std::string LName;
std::string address;
std::string phone;
};

void printInfo(Info f){
std::cout<<"The full name you entered is: "<<f.FName +" "+ f.LName<<std::endl;
std::cout<<"At address: "<<f.address<<std::endl;
std::cout<<"Phone Number: "<<f.phone<<std::endl;
}

int main(){

Info f;

std::cout<<"Enter your First Name:"<<std::endl;
std::getline(std::cin, f.FName);

std::cout<<"Enter your Last Name:"<<std::endl;
std::getline(std::cin, f.LName);

std::cout<<"Enter your address:"<<std::endl;
std::getline(std::cin, f.address);

std::cout<<"Enter your phone number:"<<std::endl;
std::getline(std::cin, f.phone);

printInfo(f);

return 0;
}
```
we can concatenate the variables using + because they are strings

- [x] **Write a program using function overloading to compute the area of a shape. Your overloaded functions should compute the area of a square, and a rectangle.** ✅ 2024-09-20
```cpp
#include <iostream>

double Area(int s){
double Sarea = s*s;
return Sarea;
}

double Area(int l, int w){
double Rarea = l*w;
return Rarea;
}

int main(){
std::cout<<"The square area is: "<<Area(3)<<std::endl;
std::cout<<"The rectangle area is: "<<Area(3,4)<<std::endl;

return 0;
}
```
- [ ] **Write a program to display the nth digit in the Fibonacci sequence. Write a function to assist you.**
```cpp
#inclue <iostream>
void FibPos(int n){

}
```
# Lab 1 - Installation and First Program
- [x] Lab #1: Installation and First Program ✅ 2024-09-19
	1. Part 1: Installation and Setup: In this part of the lab, you will install all of the necessary software to be successful in this course. We will use Linux/Unix as the OS, and EMACS as the editor in this course
	2. Windows Instructions
		- [x] Please install the Linux Subsystem on your machine: https://learn.microsoft.com/en-us/windows/wsl/install. You may choose any Linux distribution of your choice. Personally, I like Kali or Ubuntu. Alternatively, you can install Virtual Box and load the Linux distribution of your choice. ✅ 2024-09-17
		- [x] In the Linux terminal, install EMACS: https://www.gnu.org/software/emacs/download.html ✅ 2024-09-17
	3. Mac Instructions
		- Because Mac is built on the Unix OS, there is no need to install Linux, but if you choose to, you may. Virtual Box is my recommendation, and Kali or Ubuntu are my favorite Linux distributions.
		- [x] If you do not already have homebrew installed, please do that first: https://brew.sh/ ✅ 2024-09-17
		- [x] Install EMACS: https://www.gnu.org/software/emacs/download.html ✅ 2024-09-17
**The process should be the same for both systems moving forward. Make sure you**
**are using your OS’s terminal for the following steps.**
Let’s write our first program. 
- [x] Open emacs by naming the file you wish to use...navigate to the folder you want through the terminal (`cd` means change directory, you will type `cd foldername` until you are in the directory you want). ✅ 2024-09-17
- [x] Type `emacs hello.cpp` ✅ 2024-09-17
	This will open a new file in the emacs editor entitled `hello.cpp`.
- [x] **Type the following c++ program:** ✅ 2024-09-17
```cpp
#include <iostream>
#include <string>
using namespace std;
int main() {
string s;
cout << “Please enter your name: “;
getline(cin, s);
cout << “Hello “ << s << endl;
cout << “Have fun learning c++!” << endl;
return 0;}
```
- [x] Save the file by typing Ctrl-x Ctrl-c. It will ask if you wish to save the file, enter y. ✅ 2024-09-17
- [x] Try running `g++ -v`, if the c++ compiler is not already installed, proceed to step 6. Otherwise, proceed to step 7. ✅ 2024-09-17
- [x] Install the c++ compiler. ✅ 2024-09-17
	Ubuntu: https://www.codingninjas.com/studio/library/how-to-install-the-c-compiler-on-ubuntu
	Kali should come with it, but just in case: https://goacademy.io/how-to-install-c-on-ubuntu-or-kali-linux/
	Mac: https://hank.feild.org/courses/common/cpp-compiler.html
- [x] Compile the code by typing ✅ 2024-09-17
`g++ -o ./hello hello.cpp`
- [x] Execute the code by typing ✅ 2024-09-17
`./hello`
 - [x] 10.What does `–o ./hello` represent in the compilation line? ✅ 2024-09-17
 - [x] **11.Write a program that prints all even numbers from 0 to 100.** ✅ 2024-09-19
 - [x] **12.Write a program that prints whatever the user enters until the user enters the word “stop.”** ✅ 2024-09-19
 - [x] Submit your solution to number 10 and the code files for 11 and 12 in a zip file. ✅ 2024-09-19
 
# Lecture 2 - Containers
- [ ] **Write a procedure reverse that reverses the sequence of elements in a vector**
```cpp
#include <iostream>
#include <vector>

void reverse(std::vector& rev , int size)
{
std::vector reverse;
for(int i = rev.size()-1; i >=0; i--)
	{   reverse.push_back(rev[i]);
		std::cout<<reverse;
	}
}

	std::vector<int> nums = {1,2,3,4,5};
	std::vector<int> reverse;
	std::cout <<nums.size(5);

int main(){

std::vector  nums= {2,5,7,9,12};
reverse(nums, n);
std::cout<<"The reverse of the vector is: ";
for (int i=0; i<n; i++)
{ std::cout<< <<" "<<std::endl;
}

}
```
- [ ] **Write a function merge_sorted that merges two sorted vectors (as a challenge, add the sorted component)**
```cpp
#include <iostream>

```
- [ ] **Write a short program that creates a map of menu items (just add 5), display the menu to the screen, allowing the user to select two items and display the total cost of their order**
# Lecture 3 - Custom Libraries and Interfaces
- [ ] **Write the interface for the enumerated type Direction (direction.h)**
 A direction consists of NORTH, EAST, SOUTH, WEST (order is important)
- [ ] Include three helper methods
	- [ ] leftFrom (takes a direction as a parameter and returns a direction)
	- [ ] rightFrom (takes a direction as a parameter and returns a direction)
	- [ ] directionToString (takes a direction as a parameter and returns a std::string)
C++ allows you to convert an enumerated value to an integer, but the opposite direction requires a type cast
- [ ] **Try to write the implementation (direction.cpp)**
- [ ] **Designing a random number library**
	- [ ] Ability to select a random integer in a specified range
	- [ ] Ability to choose a random real number in a specified range
	- [ ] Ability to simulate a random event with a specific probability
- [ ] **Define an interface**
- [ ] **write the implementation**
- [ ] **write a client**
# Lab 2 - Git
 - [ ] Lab #2: Git
 - [ ] Navigate to the directory where you keep your lab files Ex. ~/CS300 
 - [ ] 1.Clone the CS300-lab02 repository. Type: `“git clone git@github.com:jwmcelde/CS300-lab02.git”` Or `“git clone https://github.com/jwmcelde/CS300-lab02.git”`. You can see the repositories page here: https://github.com/jwmcelde/CS300-lab02
- [ ] 2.Navigate into the newly created directory, and use `git log` to see the commit history. If you did everything right there should be 3 commits.
- [ ] 3.**Open prime.cpp, and finish writing the prime function. It should return the nth number of the prime number sequence (Ex. 1 should return 2, 3 should return 5, and 6 should return 13). Assume all inputs are valid**
- [ ] 4.While developing the function perform at least 2 commits, and give each of them an accurate description. 
	- [ ] To perform each commit you must first save the file, then add the file to the staging area with `git add <filename>`. 
	- [ ] It’s good practice to then run `git status` to make sure you added all the files you want to commit. 
	- [ ] Run `git commit -m ‘description’`  to commit your changes. 
	- [ ] You can then run `git log` to make sure your commit was successful.
- [ ] 5.After performing your commits, run `git log` and take a screenshot of the ENTIRE log. I should be able to see all the commits made on this repository. And submit this screenshot(s) to the lab02 assignment  .
- [ ] 6.Submit your finished prime.cpp program, the program must compile to get full credit  .
- [ ] 7.**Create a txt file called blazerid.txt, and answer the following questions (formatting is irrelevant as long as I can read the answers).**
	- [ ] 1.What is the difference between a local repository, and a remote repository  .
	- [ ] 2.Explain the three states of a file in git: modified, staged, and committed  
	- [ ] 3.What is a “merge conflict”  
	- [ ] 4.What command would I use to skip the staging step and commit all modified and deleted files (remember command line arguments)  
- [ ] Submit blazerid.txt repository, and a remote repository 1point.

# Lecture 4 - Initialization and References
SEE TEXT
# Lecture 5 - Strings, Patterns
- [ ] **Try to write a startswith function**
	- [ ] Takes the original string and a prefix (both strings)
	- [ ] Returns true if the string starts with the prefix
	- [ ] Returns false if not
Another common pattern should emerge
- [ ] **Can you write a reverse function?**
	- [ ] Takes a string and returns the reversed string
- [ ] 
# Lab 3 - Makefiles
You and some friends have decided to go to Nashville next weekend. Everyone has agreed to share the expenses equally, but it’s not practical to share every expense as it occurs. Thus each individual will pay for particular things, such as gas, meals, hotels, and Uber rides. After the trip all expenses will be tallied and money will be exchanged to ensure the net cost of the trip will be the same for every person, within a cent. **You’ve been tasked to create a program to compute the minimum amount of money that needs to change hands in order to equalize each person's costs. Assume the number of people in the group does not exceed 100, and the total expenses of the trip does not exceed $100,000.00** 
Examples:
Input: 10.00, 20.00, 30.00
Output: 10.00

Input: 15.00, 15.01, 3.00, 3.01
Output: 11.99
- [ ] 1.Create a main.cpp file (this will not be submitted), a trip.h file and trip.cpp file.
- [ ] 2.In the trip.h file include this function prototype: 
	- [ ] `float moneyEqualizer(std::vector<float> expenses);`
- [ ] **3.In your trip.cpp file, include a definition to this function. An automated grading system will pass a vector to this function specifying the expenses each person has made during the trip.**
	- [x] The function should return the amount of money that needs to change hands such that everyone spent an equal amount of money on the trip. ✅ 2024-10-12
		- [ ] Note: Do not include a main function in your trip.cpp file. Make sure your function is written exactly as it is above
- [ ] **4.Create a Makefile with a default target that compiles this project into an executable. The main.cpp and trip.cpp files should only be compiled if changes have been made to the source code since the last compilation.**
- [ ] 5.Include a run target in your Makefile that compiles your program then runs it.
- [ ] 6.Include a clean target in your Makefile that deletes the executable, as well as all object files in the current directory.
- [ ] 7.Submit your Makefile, trip.h file, and your trip.cpp files to canvas.
	- [ ] Note: For grading, I have created a main.cpp file that will pass test cases into your function, and check for accurate outputs. I will also use the make file you’ve provided to compile the project.
# Lecture 6 - Streams

# Lecture 7 - Classes
Write a program that implements an opposite calculator. The calculator
should add when the user types enters minus and subtract when the
user types +. It should multiply when the user types the division symbol
and divide when the user enters an asterisk. What would a class need
to do this?
- we need a class to hold the reverse methods
- we need a function to take user input

```cpp
#include <iostream>
#include <vector>

class revCalc(){
public:
std:string getInput
double revOpp();
};

class addOpp(){}:public revCalc{

}

```

# Lab 4 - Deque

# HMWK 1
Please complete the following programs. 
- [ ] Create a folder on Git called Project1. To submit the assignment, please put the link to your repo with all of your .cpp files in the Project1 folder on Github. CS300 students, please choose one problem from 1-3 and complete problems 4 and 5. **CS500 students, please choose two problems from 1-3 and complete problems 4 and 5.**
- [ ] 1.A common typing error is to place your hands on the keyboard one row to the right of the correct position. Then “Q” is typed as “W” and “J” is typed as “K” and so on. **Your task is to decode a message typed in this manner.**
	- [ ] Input: Consists of several lines of text. Each line may contain digits, spaces, uppercase letters (except “Q”, “A”, “Z’), or punctuation shown above [except back-quote (‘)]. Keys labeled with words [Tab, BackSp, Control, etc.\ are not represented in the input.
	- [ ] Output: You are to replace each letter or punctuation symbol by the one immediately to its left on the QWERTY keyboard. Spaces in the input should be echoed in the output.
Sample Input
O S, GOMR YPFSU/
Sample Output
I AM FINE TODAY.

**pseudocode:**
Q = W, W = J -> we need a map! we need to also include two keys for one output in the map, to account for upper and lower case.

We will need 2 functions:
userInput() - to take the string input, and break each part of the string to it's individual chars, return the chars
keyCorrect() - holds the map, to accept chars from userInput so that they can be converted and the proper phrase can be printed. holds map.
- How can I control the spaces? Preserve them from input to output?
	- map space char to the space char! that way we don't have to worry about taking them out and inserting them back.
```cpp
#include <iostream>
#include <string>
#include <vector>

char userInput(std::string entry){
	std::vector<char> entryChars;	
	for (char c : entry){
	entryChars.pushback(c);
	}
return entryChars;
}

keyCorrect(){
std::map<std::pair<char,char>, char> keycorrect;


}



int main(){
std::string entry;

std::cout<<"Talk to me!"<<std::endl;
std::getline(std::cin, entry);
userInput(entry);
keyCorrect(entryChars);
}

```

call the functions in the main. 

- [ ] 2.A friend of yours has just bought a new computer. Before this, the most powerful machine he ever used was a pocket calculator. He is a little disappointed because he liked the LCD display of his calculator more than the screen on his new computer (haha, as if!). To make him happy, **write a program that prints numbers in LCD display style. Be sure to use functions where appropriate.**
	- [ ] Input: The input contains several lines, one for each number to be displayed. nput:
		- [ ] Each line contains integers s and n, where n is the number to be displayed (0 <= n <= 99,999,999), and s is the size in which it shall be displayed (1 <= s <= 10). 
		- [ ] The input will be terminated by a line containing two zeros, which should not be processed.
	- [ ] Output: Print the numbers specified in the input in an LCD display-style using s “-” signs for the horizontal segments and s “|” signs for the vertical ones. 
	- [ ] Each digit occupies exactly s + 2 columns and 2s + 3 rows.
	- [ ] Be sure to fill all the white space occupied by the digits with blanks, including the last digit. There must be exactly one column of blanks between two digits.
	- [ ] Output a blank line after each number. 
Sample Input
2 12345
3 67890
00
Sample Output
![[hmwk13.png]]
--- --- ---
- [ ] 3.The reverse and add function starts with a number, reverses its digits, and adds the reverse to the original. If the sum is not a palindrome (meaning it does not give the same number read from left to right and right to left), we repeat this procedure until it does. For example, if we start with 195 as the initial number, we get 9,339 as the resulting palindrome after the fourth addition: ![[hmwk14.png]]This method leads to palindromes in a few steps for almost all of the integers. But there are interesting exceptions. 196 is the first number for which no palindrome has been found. It has never been proven, however, that no such palindrome exists.
	- [ ] **You must write a program (using functions where appropriate) that takes a given number and gives the resulting palindrome (if one exists) and the number of iterations/additions it took to find it.** 
		- [ ] You may assume that all the numbers used as test data will terminate in an answer with less than 1,000 iterations (additions) and yield a palindrome that is not greater than 4,294,967,295.
		- [ ] Input: The first line will contain an integer N (0 <= N <= 100), giving the number of test cases, while the next N lines each contain a single integer P whose palindrome you are to compute.
		- [ ] Output: For each of the N integers, print a line giving the minimum number of iterations to find the palindrome, a single space, and then the resulting palindrome itself.
Sample Input
3
195
265
750
Sample Output
4 9339
5 45254
3 6666
- [ ] 4.(CS 300 and CS 500) Suppose that you have been assigned the task of computerizing the card catalog system for a library. As a first step, your supervisor has asked you to **develop a prototype capable of storing the following information for each of 1000 books:**
	- [ ] The title
	- [ ] A list of up to five authors
	- [ ] The Library of Congress catalog number
	- [ ] A list of up to five subject headings
	- [ ] The publisher
	- [ ] The year of publication
	- [ ] Whether the book is circulating or noncirculating
- [ ] **Design the data structures that would be necessary to keep all the information required for this prototype library database.** 
	- [ ] Given your definition, it should be possible to write the declaration libraryT libdata; //This is a struct, which often uses the capital T at the end of the name to //denote that it is a structure type and have the variable libdata contain all the information you would need to keep track of up to 1000 books. 
	- [ ] Remember that the actual number of books will usually be less than this upper bound.
- [ ] **Write an additional procedure SearchBySubject that takes as parameters the library database and a subject string.** 
	- [ ] For each book in the library that lists the subject string as one of its subject headings, SearchBySubject should display the title, the name of the first author, and the Library of Congress catalog number of the book.
- [ ] **In your main, populate the data structure with five sample books.** 
	- [ ] Provide the user with a menu to add a new book, search by subject, or display a list of all of the book titles and authors.
- [ ] 5.(CS 300 and CS 500) **Write a program that plays the game of hangman.** In hangman, the computer begins by selecting a secret word at random from a list of possibilities. It then prints out a row of dashes—one for each letter in the secret word—and asks the user to guess a letter. If the user guesses a letter that appears in the word, the word is redisplayed with all instances of that letter shown in the correct positions, along with any letters guessed correctly on previous turns. If the letter does not appear in the word, the player is charged with an incorrect guess. The player keeps guessing letters until either (1) the player has correctly guessed all the letters in the word or (2) the player has made eight incorrect guesses. A sample run of the hangman program is shown below.
	- [ ] **To separate the process of choosing a secret word from the rest of the game, define and implement an interface called randword.h that exports two functions: InitDictionary and ChooseRandomWord.** 
	- [ ] InitDictionary should take the name of a data file containing a list of words, one per line, and read it into an array declared as a static global variable in the implementation.
	- [ ] ChooseRandomWord takes no arguments and returns a word chosen at random from the internally maintained array.





# Midterm
-  Compilation Process
	- [x] Source file -> compiler -> object file(s) -> linker -> executable
	- `g++ -o ./filename filename.cpp` to compile your work  - Lab 1
	- All associated files need to be in the same directory
	1. **Compiler** (g++) sequentially goes through each source code file (.cpp) in your program and does two tasks:
		1. check the code for syntax error
		2. translates the code into machine language instructions -> stored in the object file.
	2. **Linker** combines all of the object files and produces the executable file. It completes three tasks:
		1. linker reads each of the object files that are generated by the compiler to make sure they are valid
		2. linker ensures all cross-file dependencies are resolved properly. If something is defined in one .cpp file, and is used in another .cpp file, the linker **links** the two together. 
		3. the linker is also capable of linking library files - file.h
	3. **Executable** (the file you can run) is generated once the linker has finished linking all the object files and libraries
-  References
	- [x] Pass by reference
	-  Whenever you pass a simple variable from one function to another, the function gets a copy of the calling value. 
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

Here when calling function executes, it calls functionExample and passes by value myVar
in functionExample the value 10 is copied from myVar to the formal parameter inputVar so the value of nextVar will be $2*10$
the next statement changes the contents of inputVar to 4, so the output statement gives 20 and 4 
since myVar still has 10 the output statement in CallingFunction gives myvar=10

- When we want a function to return more than one value to the calling program, we pass by ref. 
	- [ ] Syntax: `void swap_values(int &variable1, int &variable2)` - here we reference variable1 and variable2 which makes copies of them in the memory, so that we can connect the values of these functions parameters to the variables that are declared in the main. 
```cpp
#include <iostream>
using namespace std;

// Function that takes a reference to an integer and doubles its value
void doubleValue(int &ref) {
    ref *= 2; // This modifies the original integer passed to the function
}

int main() {
    int value = 5;
    cout << "Original value: " << value << endl; // Output: Original value: 5
    
    doubleValue(value); // Pass 'value' by reference to the function
    
    cout << "Value after doubling: " << value << endl; // Output: Value after doubling: 10
    return 0;
}
```

- [x] Const and reference interaction - ref must be const to reference const values
-  Strings
	 - [ ] Methods such as, length(), at()
	 - [x] Access specific Chars using [] syntax
-  Basic Syntax
	 - [x] Built-in variables - **atomic data types**
	 - [x] Const - used for variables that do not change and are not to be changed by the programmer. For example: `const PI =3.14159`
		 - Has to be initialized with some value
		 - Cannot be modified
 - [x] If statement - selection statement
	 - conditional execution of code

```cpp
	if(conditional statement with boolean or value operators)
	{statements}
	elseif (conditional statement with boolean or value operators)
	{statements}
	else //<- for all other n/a conditions
	{statement to end the loop}
```

- #Recipe **Write a program using an If/else statement to validate a user input password**

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
	
- [x] **Switch statement** - takes and checks the validity of the case against the code. cases must be integer-based or enumerated constants.
	 - Useful with enums
		 - Useful for deciding between more than 2 scenarios
			 - #Recipe: **Write a program using the switch statement to determine the letter grade of a student, based on the final calculation of the grade**

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

- [x] For loop - iteration statement. Executes a statement repeatedly until the condition becomes false. Counts up or down to a value. 
	- syntax: `for (type i=0; i value comparison; i++){}`
	- Range Based For Loop: `for( range declaration : expression)`
```cpp
#include <iostream>

int main(){
	for(int i = 0; i < 5; i++)
	{std::cout<<i*i<<" "<<endl;}
return 0;
}
```

#Recipe Write a program to print the individual items in an array:
```cpp
#include<iostream>

int main(){
    char arr[] ={'a','b','c','d'};
    int n = sizeof arr;
    std::cout << "The elements of the array are: "<<std::endl;
    for (int i = 0; i < n; i++)
    {
	    std::cout << arr[i] << " "; //so that each will print on the same line
    }
	std::cout << std::endl;
}
```

- [x] While loop - iteration statement. Executes a statement until the expression evaluates to zero 
	- syntax: `while(expression is true) {do stuff}`

```cpp
#include <iostream>

int main(){
	int counter = 0;
	while(counter<=5)
	{std::cout<<"Hello World"<<std::endl;
	counter = counter +1;}
return 0;
}
```

- [ ] Function prototypes/headers vs. definitions - a function prototype 
	- #KhojSays The primary purpose of a function prototype is to ensure that a function is called correctly, in terms of both the number and types of arguments. Header files serve a broader purpose, including sharing declarations between files, reducing code duplication, and organizing code logically.
- [ ] **auto** -  deduces the type of a declared variable from its initialization expression.
	- directs the compiler to use the initialization expression of a declare variable to deduce the type.
	- use auto for most situations -- unless you really want a specific type and nothing else will do
		- use the auto keyword to declare the type instead of the regular data types
	- use auto when you want a simple way to declare a variable that has a complicated type (templates, pointers to functions, or pointers to members)
- [ ] Initialization of all types!
	 - [ ] Structured Binding - binds specific names to subobjects or elements of the initializer. Similar to a reference, it is an alias to an existing object. Unlike a reference, it does not have to be a reference type.
-  **I/O and streams**
	 - [x] What is `istream` and `ostream`
		 -  `#inclue <iostream>` header file provides basic input and output services for C++ programs
		 - it consists of two parts: `istream` (for input) and `ostream` (for output)
	 - [x] `cin` - allows user to input data   >>"data from user"
		 - syntax: `std::cin>>varName;`
		 - cin is an object that is a part of the `istream` library of functions.
		 - only reads up to the first whitespace. not good for reading sentence or multiple inputs
	 - [x] `cout` - allows programmer to print information to the screen   << "data to screen"
		 - syntax: `std::cout<<"words"<<std::endl;`
		 - cout is an object that is a part of the `ostream` library of functions.
	 - [x] `getline()` - similar to `cin` however can read the whole line, whitespace included
		 - `istream` object from which characters are extracted
		 - syntax: `getline( std::cin, string_entry, char delimeter)` - default delim is space char `" "`, so not required for spaces.
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
	  
- [ ] File i/o? 
	- `#include <fstream>`
	 - To open a file for reading or writing, instantiate an object of the appropriate file i/o class with the name of the file as a parameter. 
		 - then use the insertion operator (<<) or the extraction operator (>>) to write or read data from the file. 
			 - when you open a file you must close it as well 

```cpp
		#include <iostream>
		#include <fstream>
	int main(){
	std::ofstream outf{"sample.txt};}
```

-  Structs
	- [ ]  What are they for 
		- In C++, a structure is the same as a class except that its members are **`public`** by default
	- [ ]  How to define them
		- `struct Name {`
	- [ ]  How to instantiate them - object variables 
-  Containers
	- [ ]  Organization, Standardization, and abstraction
	- [ ]  Array
	- [ ]  Vector
		- [ ] Pros and cons
	- [ ]  List
	- [ ]  Maps
	- [ ]  Pairs
	- [ ]  Others (deque, queue, stack …)
-  Function Overloading
	- [ ]  What is it for - Polymorphism -- reduces computation time
-  Operator Overloading
	- [ ]  What is it for
-  Friend
-  Interfaces
	- [x]  What is a header file (interface)?
		- [x] How should we write our classes/functions in our header file
	- [x]  What is an implementation(file)?
		- [x] How should we write our classes/functions
	- [ ]  Interface Design Principles
		- [ ] Unified, Simple, Sufficient, General, and Stable
		- [ ] Unified Theme
-  OOP
	- [ ]  Encapsulation - using classes to "encapsulate" the data and keep the user from 
	- [ ]  Security
	- [ ]  Abstraction
	- [ ]  Reusability
-  Classes - 
	- [ ]  Public vs private
		- **public**: items that are accessible to the rest of the program
			- syntax: `public: member functions and variables`
		- **private**: items that are only accessible to other functions within the parent class
			- syntax: `private: member functions and variables`
	- [ ]  Constructors - special member functions of a class that are execute whenever a new object of that class is created. They serve to  initialize the object, often by setting initial values to member variables.
		- The constructor is like a instance of a class, and we can also initialize it with values as parameters. 
		- It often
	- [ ]  Syntax (again make sure you understand how to use interfaces to write your classes)
-  Inheritance - allows a class to inherit properties and methods from another class (parent class)
	- [ ]  Abstract Classes
		- [ ] How to write an abstract class
		- [ ] What is the purpose of an abstract class
	- [ ]  Virtual functions
		- [ ] Remember Pure-virtual vs Virtual
	- [ ]  How to handle your constructors
	- [ ]  Pros and cons of inheritance
	- [ ]  Polymorphism
		- [ ] Understand object slicing
-  Pointers
	- [ ]  Dereference
	- [ ]  Declaration
	- [ ]  Nullptr
-  Memory Management
	- [ ]  new and delete
- Sample Questions

Exam Review
**Q: The auto keyword determines the type of a variable during runtime (T/F)**
A: False (the type is determined at compile-time)

**Q: You can dereference a reference to obtain the original**
**value using the * operator (T/F)** - NO that's for pointers. You don't need to dereference a reference. The reference makes a copy of the actual variable that needs to be used. 
- A: False (trick question, there is no need to dereference a reference)

**Q: A const variable must be initialized with some value. (T/F)** - YES and it must not change, which is why it needs to be initialized. 
- True!

**Q: Runtime polymorphism is not a feature of C++
(Polymorphism must be determined at compile time) (T/F)** - FALSE. Polymorphism is set before complie time, during the writing process. 
- False

**Q: Structs may include member functions**
A: True

**Q: A function can have several versions, each with a unique header/prototype that specifies different combinations of arguments that can be passed to it. (T/F)** - YES. Say i wanted to calculate the area of a three different shapes. Using function overloading (what this describes) allows me to keep my code concise and use the same function NAME with different formulas so that each area can be properly calculated. 
- True (this is function overloading)

Q: How do you create an abstract class in C++
A: You include a Pure-virtual function in the class. Ex.
virtual void draw() const = 0;

**Q: What do we include in header files(interfaces)**

#KhojSays 
In C++ programming, a `.h` file, also known as a header file, is typically used to declare the interface to a set of functionalities that a C++ file (`.cpp`) provides. This includes class declarations, function prototypes, constants, and type definitions. The actual implementation of these functionalities, especially the definitions of class methods, is usually placed in a corresponding `.cpp` file. 

Class Declarations in Header Files
A class declaration in a header file typically includes:
- The class name.
- Its member variables (often private or protected for encapsulation).
- Declarations of its methods (functions).

Here's an example of what might be in a `.h` file:

```cpp
#ifndef _bankaccount_
#define _bankaccount_

#include <string>

class BankAccount{

public:
	BankAccount();
	BankAccount(std::string name, double bal);
	
	void deposit(double amount);
	void withdraw(double amount);
	double getBalance();
	std::string printStatement();


private:
	std::string accountHolder;
	double balance;

friend bool operator==(BankAccount one, BankAccount two);

};



#endif
```

 Class Definitions in Source Files
The corresponding `.cpp` file would then provide the definitions for the constructor and methods declared in the header:

```cpp
#include "bankAccount.h"
#include <string>

BankAccount::BankAccount(){
	accountHolder = "";
	balance = 0;
}

BankAccount::BankAccount(std::string name, double bal){
	accountHolder = name;
	balance = bal;

}

void BankAccount::deposit(double amount){
	balance += amount;
}

void BankAccount::withdraw(double amount){
	if(amount <= balance)
		balance -= amount;

}

double BankAccount::getBalance(){
	return balance;
}

std::string BankAccount::printStatement(){
	return "Account Holder" + accountHolder _ "\nBalance:"
	std::to_string(balance);
}

bool operator==(BankAccount one, BankAccount two);
{ return one.getBalance() == two.getBalance();

}
```

The main .cpp file - holds all the actions to perform/data to send 
```cpp
#include <iostream>
#include "bankAccount.h"

int main() { 
  BankAccount account1("John Doe", 1000);
  BankAccount account2("Sally Joe", 500);
  std::cout << account1.printStatement() << std::endl;
  std::cout << account2.printStatement() << std::endl;
  if(account1 == account2)
    std::cout << "Equal";
  else
    std::cout << "Not equal";
}
```


Inline Definitions
It's also possible to define functions, including class methods, directly within a header file. This is often done for template classes or inline functions, where the definition must be available to the compiler at compile time. However, for regular class methods, defining them in the header file can lead to longer compile times and potential issues with multiple definitions if the header is included in multiple places without proper guards.

A: Function prototypes/headers, or class prototypes/headers

**Q: What do we include in implementations (.cpp files with no main function)**
.cpp with no main function - holds the definitions for all the functions and inheritance stuff
.h - holds class definitions for all the functions and inheritance levels
.cpp with main - does the actions. depends on the other files to perform commands listed within the main.

A: Definitions for functions, and member functions

Q: What is the # symbol used for in c++
A: A preprocessor directive, Examples
● Include statements
● Macros
● Header guards

Q: **Encapsulation is something we want to avoid in OOP (T/F)** - NO. The ability to hide the details from the user of your code and encapsulate everything under a clear interface is a great advantage.
Data is encapsulated within a class.
A: False (it is one of the major advantages of OOP)

**Q: What is a virtual function?** - a function whose behavior can be overridden in child classes. As oppose to non-virtual functions, the overriding behavior is preserved even if there is no compile-time information about the actual type of the class

A: a function that may be overwritten in child classes

Q: What is a pure virtual function
A: A function that must be overridden in child classes

Short Answer: What are some of the advantages of using Inheritance? What are
some of the disadvantages
Promotes code reuse. 
makes it easy to extend the base class's functionality. a derived class can add its own fields and methods in addition to inherited ones
a derived class can override a method from its base clss to provide a specific implementation of that method.
Inheritance enables polymorphism where a single interface can represent different underlying data types
data encapsulation and allows for abstraction

Deep inheritance heiracrhies are too complicated to navigate
overriding issues - can lead to unexpected behavior if not done correctly can cause errors and make the code hard to debug (bc two things are named the same but doing different things)
increased complexity
tight coupling - making it difficult to change one class without affecting other classes


#KhojSays 
```cpp
#include <iostream>
using namespace std;

// Base class
class Animal {
public:
    void eat() {
        cout << "I can eat!" << endl;
    }
};

// Derived class
class Dog : public Animal {
public:
    void bark() {
        cout << "I can bark! Woof woof!" << endl;
    }
};

int main() {
    Dog myDog;
    myDog.eat();  // Calling function from base class
    myDog.bark(); // Calling function from derived class
    return 0;
}
```

```cpp
void hanoi(char start, char spare, char end, int n){
//base case
if (n==0)
return 0;
else
hanoi(start, end ,spare, n-1);
std::cout<<start<<"->"<<end<<std::endl;
hanoi(spare,start,end,n-1);
}
```
spare will alternate based on how we begin **take some time to understand how the game works**

binary search as a recursive process
choose element in the middle of the range
if this element is our target, success!
if element is less than our target, do binary search from middle to end


# Lab 7-8
Trapped in a labyrinth, and only escape is correct path
spellbook
potion
wand

Pointer maze - maze consists of a collection of objects of type MazeCell:

struct MazeCell{
	Item whatsHere; <- obj to hold whatever item is present, if any
	MazeCell* north; <- pointer to the north direction variable
	MazeCell* south;
	MazeCell* east;
	MazeCell* west;
};

Item is of enumerated type: 
enum class Item{
	NOTHING, SPELLBOOK, POTION, WAND;
};


The MazeCell you begin at would have its north, south, east, and west pointers pointing
at MazeCell objects located one step in each of the directions from your start. 

MazeCell containing SPELLBOOK would have its north, east, west pointers set to nullptr
bc it is a dead end. Similar logic flows througout

There are many paths to exit, we take a string and use the letters as directions:
"ESNWWNNEWSSESWWN" 
"SWWNSEENWNNEWSSEES" 
"WNNEWSSESWWNSEENES"

We need to write a function that given a cell in a maze and a string path, checks whether
that path is legal and picks up all three items. 

`bool isPathToFreedom(MazeCell* startLocation, const std::string& path)`
we will need `std::string path = "ESNWWNNEWSSESWWN"`
- break the string into directions
- NSEW, Which is a valid direction? An invalid direction should give an error message. 
	- If the direction is valid, move to the next node in the maze.
	- Some kind of structure to store 
- recursive function calls because we will need to validate each step

Function takes as input, start location in the maze, and a string of NSEW, then returns whether that path lets you escape from the maze. 
It will work if the path is 1. legal, and 2. the path picks up SPELLBOOK, WAND, and POTION along the way

assume start location is not nullptr
1. E - first move. If E is valid, move on to next step, else display error messsage
2. S 
3. N
4. W
5. W
6. ...NNEWSSESWWN

Use the pointer structure to "move" through the maze
if the pointer goes to a dead end, return false, dead ends are  `nullptr`
else the pointer goes to a valid direction, and move on to 

