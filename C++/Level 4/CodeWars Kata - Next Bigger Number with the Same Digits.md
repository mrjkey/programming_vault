# CodeWars Kata - Next Bigger Number with the Same Digits

[Link to the kata](https://www.codewars.com/kata/55983863da40caa2c900004e/train/cpp)

## Problem Statement

Create a function that takes a positive integer and returns the next bigger number that can be formed by rearranging its digits. For instance:

```
  12 ==> 21
 513 ==> 531
2017 ==> 2071
```

If the digits can't be rearranged to form a bigger number, return `-1`:

```
  9 ==> -1
111 ==> -1
531 ==> -1
```

## Solution

**Code**:
```cpp
#include <algorithm>
#include <string>

long nextBigger(long n) {
    std::string digits = std::to_string(n);

    // Find the first digit from the right that is smaller than the digit to its right
    auto pivot = std::prev(digits.end());
    while (pivot != digits.begin() && *pivot <= *(std::prev(pivot))) {
        --pivot;
    }

    // If no such digit is found, it's the largest permutation
    if (pivot == digits.begin()) {
        return -1;
    }
    --pivot; // Move pivot to the actual smaller element

    // Find the smallest digit to the right of the pivot that's larger than the pivot
    auto change = std::find_if(digits.rbegin(), std::make_reverse_iterator(pivot), 
                               [pivot](char c) { return c > *pivot; });

    std::swap(*pivot, *change);
    
    // Sort the digits after the pivot in non-decreasing order
    std::sort(pivot + 1, digits.end());

    return std::stol(digits);
}
```

**Explanation**:

- Convert the number to a string for easier digit manipulation.
- Traverse the digits from right to left to find the first digit which is smaller than the one on its right.
- If such a digit is not found, it's the highest arrangement, so return `-1`.
- Traverse from right to left again to find the smallest digit that is larger than the found digit.
- Swap these two digits.
- Sort the digits to the right of the found digit in ascending order.
- Convert the string back to a number and return it.

## Key Concepts

- `std::prev`: Returns an iterator pointing to the element located n positions before the element iterator currently points to.
- `std::find_if`: Finds the first element satisfying specific criteria in a given range.
- `std::swap`: Exchanges values of two objects.
- `std::sort`: Sorts elements in a range.
- `std::stol`: Converts a string to a long integer.

## Tags

#std/algorithm #std/string #conversion #iteration

---