# CodeWars Kata - Check X and O

## Link
[kata link](https://www.codewars.com/kata/55908aad6620c066bc00002a/train/cpp)

## Problem Statement
Check to see if a string has the same amount of 'x's and 'o's. The method must return a boolean and be case insensitive. The string can contain any char.

Examples input/output:
```
XO("ooxx") => true
XO("xooxx") => false
XO("ooxXm") => true
XO("zpzpzpp") => true // when no 'x' and 'o' is present should return true
XO("zzoo") => false
```

## Solution

### Code
```cpp
#include <algorithm>
#include <cctype>

bool XO(const std::string& str)
{
    auto count_x = std::count_if(str.begin(), str.end(), [](char c) {
        return std::tolower(c) == 'x';
    });
    
    auto count_o = std::count_if(str.begin(), str.end(), [](char c) {
        return std::tolower(c) == 'o';
    });

    return count_x == count_o;
}
```

### Explanation
The solution leverages the `std::count_if` function from the STL to count occurrences of 'x' and 'o' in the given string. The `std::tolower` function ensures that the comparison is case-insensitive. After counting occurrences of both characters, we simply compare their counts and return if they are equal.

## Key Concepts

- `std::count_if`: An algorithm in the C++ STL that counts the number of elements in a range that satisfy a specific predicate.
- `std::tolower`: A function that converts the given character to lowercase. Useful for making character comparison case insensitive.

## Tags
#std/algorithm #std/string #lambda-expression #case-insensitivity
```

You can copy and paste the above content directly into an Obsidian note. The code section is wrapped appropriately in "```" to indicate a code block.