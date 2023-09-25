

# CodeWars Kata - Pig Latin Transformation

[Placeholder Link to Kata](https://www.codewars.com/kata/520b9d2ad5c005041100000f/train/cpp)

## Problem Statement
Move the first letter of each word to the end of it, then add "ay" to the end of the word. Leave punctuation marks untouched.
Examples:
- `pigIt('Pig latin is cool')` should return `igPay atinlay siay oolcay`
- `pigIt('Hello world !')` should return `elloHay orldway !`

## Solution

### Solution Code
```cpp
#include <sstream>
#include <algorithm>
#include <cctype>
#include <string>

std::string pig_it(std::string str)
{
    std::istringstream ss(str);
    std::string word, result;

    while (ss >> word)
    {
        // If the word is not a punctuation
        if (!std::ispunct(word[0]))
        {
            // Rotate the word left by one position.
            std::rotate(word.begin(), word.begin() + 1, word.end());
            word += "ay";
        }

        result += word + " ";
    }

    // Remove the trailing space and return.
    return result.substr(0, result.size() - 1);
}
```

### Explanation
1. An input string stream (`std::istringstream`) is used to extract words from the given string `str`.
2. For each extracted word, check if its first character is punctuation using `std::ispunct`.
3. If not punctuation, rotate the first character to the end using `std::rotate` and append "ay".
4. Add the transformed word (or unchanged punctuation) to the `result` string.
5. Before returning, remove the trailing space from the result using `std::string::substr`.

## Key Concepts
- **`std::istringstream`**: This is a stream class to operate on strings. It allows treating a string as a stream and extracting words or tokens from it.
- **`std::rotate`**: An STL algorithm that rotates the elements in the range in such a way that the element at the middle becomes the new first element.
- **`std::ispunct`**: A function to check if a character is a punctuation character.
- **`std::string::substr`**: Used to extract a substring from the given string.

## Tags
#std/istringstream #std/rotate #std/ispunct #std/string


## Alternate Solutions:

```c++
#include <string>
#include <regex>
using namespace std;
string pig_it(string Z) {
    regex reg(("(\\w)(\\w*)(\\s|$)"));
    return regex_replace(Z, reg, "$2$1ay$3");
}
```

