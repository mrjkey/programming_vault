# CodeWars Kata - accum

[Link to the kata](https://www.codewars.com/kata/5667e8f4e3f572a8f2000039/train/cpp)

## Problem Statement

Given a string, the function should return a new string where for every character in the original string, it is transformed into uppercase and followed by the same character in lowercase repeated according to its position (0-indexed). Each group of characters should be separated by a hyphen (`-`).

**Examples:**

- `accum("abcd")` should return "A-Bb-Ccc-Dddd"
- `accum("RqaEzty")` should return "R-Qq-Aaa-Eeee-Zzzzz-Tttttt-Yyyyyyy"
- `accum("cwAt")` should return "C-Ww-Aaa-Tttt"

## Solution

```cpp
#include <string>
#include <sstream>
#include <cctype>
#include <algorithm>

class Accumul
{
public:
    static std::string accum(const std::string &s) {
        std::ostringstream oss;
        
        for(size_t i = 0; i < s.size(); ++i) {
            oss << char(std::toupper(s[i]))  // Uppercase version of the character
                << std::string(i, char(std::tolower(s[i]))); // Repeated lowercase version

            if(i != s.size() - 1) oss << '-';  // Append '-' if it's not the last element
        }
        
        return oss.str();
    }
};
```

**Explanation:**

1. An `ostringstream` is utilized to efficiently concatenate strings together.
2. Iterate over the input string's characters using a loop.
3. For each character at the position `i`, transform it to uppercase using `std::toupper` and append to the stream.
4. Add the same character in lowercase (converted using `std::tolower`) repeated `i` times using the string repetition constructor.
5. If it's not the last character, append a '-' to the stream.

## Key Concepts

- `std::ostringstream`: A stream used for operations on strings, efficient for multiple string concatenations or manipulations.
- `std::toupper` and `std::tolower`: Functions from `<cctype>` to change the case of individual characters.
- `std::string`: The repetition constructor of this container creates a string with a character repeated a specified number of times.

## Tags

- `#std/ostringstream`
- `#std/toupper`
- `#std/tolower`
- `#std/string`
- `#algorithm`
- `#string-manipulation`

---