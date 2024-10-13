

1. How populate a vector with numbers
	1. For each `i` in $[0,9]$, place those values into the vector `vec` with `vec.push_back(i)`
```cpp
std::vector<int> vec;
    for(int i = 0; i < 10 ; i++){
        vec.push_back(i);
    }
```
2. How to display the individual items in a vector
	1. for each `i` in `vec.size()`, display the ith element of vector `vec`
```cpp
  std::vector<int> vec; //can initialize vector here
  for(unsigned int i = 0; i < vec.size(); i++){
        std::cout << vec[i] << std::endl;
    }
```
3. Putting it all together - Display function for a vector
	1. In the `main()` - declare a vector `v`
	2. show that the vector `v` is empty, using `v.size()`, output statement
	3. Indicate that the vector is being populated
		1. initialize for loop to populate vector `v` using `v.push_back(i)`
	4. show that the vector `v` is not empty, using `v.size()`, output statement
	5. pass vector `v` to the `display(v)` function by reference:
		1. `void display (std::vector<int>&v)`
	6. In `display()` - initialize a for loop to print each element in vector `v`.  
		1. `" "` prints a space between each value
		2. displays an empty line after the loop completes: `std::cout<<"/n"<<std::endl;`. 
	7. In `main()` - add another value to vector v with `push_back(5)`
	8. show that the vector v is larger by 1 element, `v.size()`, output statement 
	9. call `display(v)` again, to print new vector v, with added value  
```cpp
#include <iostream>
#include <vector>

void display(std::vector<int> &v)
{
    for(unsigned int i=0; i<v.size(); i++)
    {
        std::cout << v[i] << " ";
    }
    std::cout << "\n" << std::endl;
}

int main()
{
    std::vector<int> v;
    std::cout << "Size of Vector=" << v.size() << std::endl;

    //Putting values into the vector
    std::cout << "populating the vector..." << std::endl;
    for(int i=0; i<5; i++)
    {
        v.push_back(i);
    }
    //Size after adding values
    std::cout << "Size of Vector=" << v.size() << std::endl;

    //Display the contents of vector
    display(v);

    v.push_back(6);

    //Size after adding values
    std::cout << "Size of Vector=" << v.size() << std::endl;

    //Display the contents of vector
    display(v);

}
```

### Lab 3
main.cpp file (this will not be submitted), a trip.h file and trip.cpp file.
trip.h file - function prototypes
```cpp
#ifndef_trip.h_
#def_trip.h_

float moneyEqualizer(std::vector<float> expenses);

```


`#include trip.h`
`float moneyEqualizer(std::vector<float> expenses);`
`expenses` is a vector!
trip.cpp file:
```cpp
#include <iostream>
#include <algorithm>
#include <vector>

float moneyEqualizer(std::vector<float> &expenses){
int z = expenses.size();
std::sort(expenses.begin(),expenses.end(),std::greater<float>());

std::vector<float> diff;
for(int i=0; i<z;i++){
    diff.push_back(expenses[i]-expenses[i+1]);
    //std::cout<<diff[i]<<std::endl;
}
std::sort(diff.begin(),diff.end(),std::greater<float>());
float equal = 0.0;
equal = diff[0];
//std::cout<<equal<<std::endl;

return equal;
}


int main(){
std::vector<float> expenses;
float x;
int n;
std::cout<<"enter how many people went:"<<std::endl;
std::cin>>n;

for(int i=0; i<n; i++)
{std::cout<<"Enter each person's expenses:"<<std::endl;
std::cin>>x;

expenses.push_back(x);
}
std::cout<<"\n"<<std::endl;

std::cout<<"the minimum amount to send is: "<<moneyEqualizer(expenses)<<std::endl;

return 0;
}
```

automated grading system will pass a vector to this function specifying each person's expenses during the trip
return - amnt of money that needs to change hands so that everyone spends an equal amount on the trip. 

trip.h file
prototype - `float moneyEqualizer(std::vector<float> expenses);`

main.cpp

