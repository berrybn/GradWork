user input: several lines of garbled text. the text is generated through a typing error where q is typed as w and j is typed as k - shifted 1 key over to the left. 

row0 = {234567890-=}
row00 = {1234567890-}

row1={wertyuiop[]\}
row11={qwertyuiop\[}

row2= {sdfghjkl;}
row22={asdfghjkl}

row3={xcvbnm,.}
row33={zxcvbnm,}

o s, gomr ypfsu **/** escape character  
I am fine today


we need to cycle thru the letters of each row. We also need to have the location of the button (row0, row1, row2, row3) to validate

for(letters:row0)
if input ismember of row#
use corresponding cypher

input a, decide if it is in a row, find its location in the row, and print the character next to it 
row2 = {asdfghjkl;}
if x ismember of row2
for i< length(row2)
cout<<row2(i+1)

Issues
Looping through arrays will be tedious, and call for a lot of data entry set up, that feels wrong-- but i can probably make it work

Figure out how maps work

i need to be able to input a string!! so I'm not using individual characters, or even string chars. 

```cpp
#include <iostream>
#include <map>
#include <string>

std::map<char, char> type_error = {
    { 'A', '1' },
    { 'B', '2' },
    { 'C', '3' }
};


int main()
{
    std::string entry;
    std::string row2[10] = {"a","s","d","f","g","h","j","k","l",";"};
    std::cout << "letter entry: ";
    stdd::cin >> entry;

    for (int i = 0; i < 10; i++)
    {
        if(row2[i] == entry)
        {
            std::cout << entry << " was found in the array." << std::endl;
            return 0;
        }
    }

    std::cout << entry << " wasn't found in the array." << std::endl;
    return 0;
}
```

