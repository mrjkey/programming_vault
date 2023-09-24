# CodeWars Kata - Odd Integers

[Placeholder for Kata Link](https://www.codewars.com/kata/54da5a58ea159efa38000836/train/cpp)

## Problem Statement

Given an array of integers, find the one that appears an odd number of times. There will always be only one integer that appears an odd number of times.

Examples:
- `[7]` should return `7`, because it occurs 1 time (which is odd).
- `[0]` should return `0`, because it occurs 1 time (which is odd).
- `[1,1,2]` should return `2`, because it occurs 1 time (which is odd).
- `[0,1,0,1,0]` should return `0`, because it occurs 3 times (which is odd).
- `[1,2,2,3,3,3,4,3,3,3,2,2,1]` should return `4`, because it appears 1 time (which is odd).

## Solution

```cpp
#include <vector>
#include <numeric>

int findOdd(const std::vector<int>& numbers) {
    return std::accumulate(numbers.begin(), numbers.end(), 0, [](int acc, int n) {
        return acc ^ n;
    });
}
```

### Explanation

To solve the given problem, we employ the property of the XOR bitwise operation. When the same number is XORed with itself, the result is `0`. When a number is XORed with `0`, it remains unchanged.

For any number appearing an even number of times in the list, XORing them will result in `0`. Consequently, only the number that appears an odd number of times will remain after XORing all the elements.

Using `std::accumulate` from the `<numeric>` header is an idiomatic way to aggregate values from a container in C++. We traverse the input list and apply the XOR operation for each number, accumulating the result.

## Key Concepts

- **`std::accumulate`**: A function that aggregates values from a container. It can be found in the `<numeric>` header. In this kata, it's used to apply the XOR operation across the elements of the list.
- **XOR Bitwise Operation**: A binary operation that returns `0` when both bits are the same and `1` when they are different.

## Tags

- `#std/vector`
- `#std/accumulate`
- `#bitwise-operation`
- `#xor`
- `#algorithm`

---