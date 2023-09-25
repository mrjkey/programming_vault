# CodeWars Kata - Descending Order Sort

[Link to the Kata](https://www.codewars.com/kata/5467e4d82edf8bbf40000155/train/cpp)

## Problem Statement

Your task is to make a function that can take any non-negative integer as an argument and return it with its digits in descending order. Essentially, rearrange the digits to create the highest possible number.

Examples:
- Input: 42145 Output: 54421
- Input: 145263 Output: 654321
- Input: 123456789 Output: 987654321

## Solution

```cpp
#include <cinttypes>
#include <string>
#include <algorithm> // for std::sort

uint64_t descendingOrder(uint64_t a) {
    // Convert the integer to a string
    std::string numStr = std::to_string(a);

    // Sort the string in descending order using std::sort
    std::sort(numStr.begin(), numStr.end(), std::greater<>());

    // Convert the string back to uint64_t using std::stoull (string to unsigned long long)
    return std::stoull(numStr);
}
```

**Explanation**:

1. Convert the input number to a string using `std::to_string`.
2. Sort the string in descending order using the STL's `std::sort` function with the comparator `std::greater`.
3. Convert the sorted string back to a number using `std::stoull`.

## Key Concepts

- `std::to_string`: Converts various data types, including numeric types, to a string.
- `std::sort`: Sorts the elements in a range [begin, end) in the order defined by the given comparator.
- `std::stoull`: Converts a string to an unsigned long long integer.

## Tags

#std/string #std/algorithm #std/sort #integer #string #sorting


## Alternate

```c++
#include <cinttypes>
#include <string>
#include <algorithm>

uint64_t descendingOrder(uint64_t a)
{
  std::string s = std::to_string(a);
  std::sort(s.rbegin(), s.rend());
  return std::stoull(s);
}
```