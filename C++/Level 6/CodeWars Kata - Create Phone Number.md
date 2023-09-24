
CodeWars Kata - Create Phone Number

**Link**: [Placeholder for kata link](https://www.codewars.com/kata/525f50e3b73515a6db000b83/train/cpp)

---

### Problem Statement

Write a function that accepts an array of 10 integers (between 0 and 9), that returns a string of those numbers in the form of a phone number.

Example: `createPhoneNumber(int[10]{1, 2, 3, 4, 5, 6, 7, 8, 9, 0})` should return `"(123) 456-7890"`. The returned format must be correct to complete this challenge. Don't forget the space after the closing parentheses!

---

### Solution

```cpp
#include <string>
#include <cstdio>

std::string createPhoneNumber(const int arr[10]) {
    char buffer[15];
    std::sprintf(buffer, "(%d%d%d) %d%d%d-%d%d%d%d", 
                 arr[0], arr[1], arr[2], arr[3], arr[4], arr[5], arr[6], arr[7], arr[8], arr[9]);
    return std::string(buffer);
}
```

**Explanation**:
The solution uses the `std::sprintf` function to format the 10 integers into the required phone number format. The format specifier `"%d"` is used for each integer in the `arr`. The formatted result is stored in the `buffer`, which is then converted to a `std::string` before being returned.

---

### Key Concepts

- **std::sprintf**: This is a function from the C Standard Library (`<cstdio>`) that writes formatted output to a `char` array based on a format string and a variable number of arguments. It's a powerful tool for string manipulation, especially when dealing with different data types.

---

**Tags**: `#cpp` `#std/cstdio` `#string-formatting`

---