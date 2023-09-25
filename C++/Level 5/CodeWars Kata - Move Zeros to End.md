# CodeWars Kata - Move Zeros to End

[Link Placeholder](https://www.codewars.com/kata/52597aa56021e91c93000cb0/train/cpp)

## Problem Statement

Write an algorithm that takes an array and moves all of the zeros to the end, preserving the order of the other elements.

Example:
```
move_zeros({1, 0, 1, 2, 0, 1, 3}) // returns {1, 1, 2, 1, 3, 0, 0}
```

## Solution

### Code:
```cpp
#include <vector>
#include <algorithm>  // For std::stable_partition

std::vector<int> move_zeroes(const std::vector<int>& input) {
    std::vector<int> result = input;  // Create a copy of the input
    std::stable_partition(result.begin(), result.end(), [](int n){ return n != 0; });
    return result;
}
```

### Explanation:
The problem is solved using the `std::stable_partition` algorithm from the C++ Standard Template Library (STL). This algorithm reorders elements based on a predicate, keeping the relative order of elements intact. In our case, the predicate is a lambda function that returns `true` for non-zero elements and `false` for zero elements. As a result, all non-zero elements are moved to the front, and zeros are moved to the end.

## Key Concepts

- **std::stable_partition**: An STL algorithm that partitions the range into two segments based on a predicate. The first segment contains all elements for which the predicate is true, and the second segment contains all elements for which the predicate is false. The relative order of elements in both groups is preserved.
- **Lambda Functions**: Unnamed functions defined inline. In our solution, we used a lambda function to define the predicate for `std::stable_partition`.

## Tags

- `#std/vector`
- `#std/algorithm`
- `#lambda`
- `#partition`

---