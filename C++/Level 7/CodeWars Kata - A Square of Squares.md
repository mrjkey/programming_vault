# CodeWars Kata - A Square of Squares

[Link to the kata](https://www.codewars.com/kata/54c27a33fb7da0db0100040e/train/cpp)

## Problem Statement

You like building blocks. Especially square ones. Determine if a given integral number is a perfect square. In mathematics, a square number or perfect square is an integer that is the square of another integer.

**Examples**:

- -1  =>  false
-  0  =>  true
-  3  =>  false
-  4  =>  true
- 25  =>  true
- 26  =>  false

## Solution

```cpp
#include <cmath>

bool is_square(int n) {
    if (n < 0) {
        return false;  // Negative numbers cannot be square numbers
    }
    
    // Compute the square root
    double root = std::sqrt(n);
    
    // Check if the square root is an integer
    return root == static_cast<double>(static_cast<int>(root));
}
```

**Explanation**:

1. First, check if the given number `n` is negative. If so, it can't be a perfect square.
2. Calculate the square root of `n` using `std::sqrt`.
3. Check if the computed square root is an integer. If the original value of `root` was an integer (i.e., a perfect square root), then it will match its double-casted integer value.

## Key Concepts

- `std::sqrt`: A function from the `cmath` library that returns the non-negative square root of its argument.
- Type Casting: Using `static_cast<>()` to convert between types. In this case, we cast from `double` to `int` to truncate any fractional part, and then back to `double` to compare with the original value.

---

Tags: 
- `#integer`
- `#math`
- `#std/cmath`
- `#type-casting`

---

## Alternate

```c++
#include<cmath>

bool is_square(int n) {
  if (n < 0) return false;
  int square = sqrt(n);
  return square * square == n;
}
```

```c++
#include <cmath>

bool is_square(int n)
{
  return fmod(sqrt(n), 1) == 0;
}
```