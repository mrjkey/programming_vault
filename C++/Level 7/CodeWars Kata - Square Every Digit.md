
Title: **CodeWars Kata - Square Every Digit**

Link: [Link to Kata](https://www.codewars.com/kata/546e2562b03326a88e000020/train/cpp)

---

## Problem Statement

You are tasked with squaring every digit of a number and then concatenating them.

Examples:
- Input: 9119 | Output: 811181 (because 92 is 81 and 12 is 1)
- Input: 765  | Output: 493625 (because 72 is 49, 62 is 36, and 52 is 25)

---

## Solution

**Code**:

```cpp
#include <string>

int square_digits(int num) {
    std::string num_str = std::to_string(num);
    std::string result;

    for(char c : num_str) {
        int squared = (c - '0') * (c - '0');
        result += std::to_string(squared);
    }

    return std::stoi(result);
}
```

**Explanation**:
1. Convert the integer input to its string representation to handle each digit separately.
2. Iterate over each character in the string. For each digit, compute its square and append the squared result to a new string, `result`.
3. Convert the final concatenated `result` string back to an integer and return it.

---

## Key Concepts

- **String Conversion**: Used `std::to_string` and `std::stoi` from the `<string>` header to convert between integers and their string representations.
- **Character to Integer Conversion**: Converted a digit character to its integer value using `(c - '0')` for operations.

---

**Tags**: `#std/string` `#string-manipulation`

---


## Alternate

```c++
int square_digits(int n) {
  int a = 1;
  int m = 0;
  while (n > 0) {
    int d = n % 10;
    m += a * d * d;
    a *= d <= 3 ? 10 : 100;
    n /= 10;
  }
  return m;
}
```


