# CodeWars Kata - ROT13

[Link Placeholder to the Kata](https://www.codewars.com/kata/530e15517bc88ac656000716/train/cpp)

## Problem Statement

ROT13 is a simple letter substitution cipher that replaces a letter with the letter 13 letters after it in the alphabet. ROT13 is an example of the Caesar cipher. Create a function that takes a string and returns the string ciphered with Rot13. If there are numbers or special characters included in the string, they should be returned as they are. Only letters from the Latin/English alphabet should be shifted, like in the original ROT13 "implementation".

## Solution

```cpp
#include <string>
#include <algorithm>
using namespace std;

string rot13(string msg) {
    transform(msg.begin(), msg.end(), msg.begin(),
        [](char c) -> char {
            if (c >= 'A' && c <= 'Z') {
                return (c - 'A' + 13) % 26 + 'A';
            }
            if (c >= 'a' && c <= 'z') {
                return (c - 'a' + 13) % 26 + 'a';
            }
            return c;
        }
    );
    return msg;
}
```

**Explanation**:
- The `std::transform` function is used to apply a function to each character of the string. 
- Inside the lambda function:
  - For uppercase letters, we shift the character by 13 places. The expression `(c - 'A' + 13) % 26` calculates the shift and ensures we wrap around after 'Z'. Adding back `'A'` gives us the appropriate ASCII value.
  - A similar operation is done for lowercase letters.
  - Non-alphabet characters are returned as they are.

## Key Concepts

- `std::transform`: This is an STL algorithm that applies a given function to a range of input elements and stores the result in an output range.
- Lambda Functions: These are anonymous functions in C++. They can capture variables from their enclosing scope, providing a convenient way to pass information into a function.
- Character Manipulation: Basic arithmetic operations can be applied directly to characters in C++, which internally uses their ASCII values.

## Tags

- `#std/transform`
- `#lambda-functions`
- `#character-manipulation`
- `#c++`

---

## Alternate solution

```c++
std::string rot13(std::string msg)
{
  for(auto& x : msg) 
    if (islower(x)) x = 'a'+(x-'a'+13)%26; 
    else if(isupper(x)) x = 'A'+(x-'A'+13)%26;
  return msg;
}
```

