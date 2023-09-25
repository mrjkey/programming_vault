# CodeWars Kata - Maximum Sum Subarray

[Link Placeholder](https://www.codewars.com/kata/54521e9ec8e60bc4de000d6c/train/cpp)

## Problem Statement

The maximum sum subarray problem consists of finding the maximum sum of a contiguous subsequence in an array or list of integers. For instance:

```cpp
maxSequence({-2, 1, -3, 4, -1, 2, 1, -5, 4});
```
This should return 6, representing the sequence {4, -1, 2, 1}. 

An easy case is when the list is made up of only positive numbers and the maximum sum is the sum of the whole array. If the list is made up of only negative numbers, return 0 instead. An empty list is considered to have a zero greatest sum.

## Solution

### Code:
```cpp
#include <vector>
#include <algorithm> // for std::max

int maxSequence(const std::vector<int>& arr){
    if(arr.empty()) return 0; // Return 0 for empty array.
    
    int max_so_far = 0; 
    int max_ending_here = 0;
    
    for(int num : arr){
        max_ending_here = std::max(num, max_ending_here + num);
        max_so_far = std::max(max_so_far, max_ending_here);
    }
    
    return std::max(max_so_far, 0); // Ensure non-negative return.
}
```

### Explanation:
- The function checks for an empty array and returns 0 immediately for such cases.
- We use Kadane’s algorithm to efficiently find the maximum sum subarray in linear time. The algorithm maintains two key values, `max_so_far` and `max_ending_here`.
- For every element in the array, we update `max_ending_here` to be the greater value between the current element and the sum of `max_ending_here` and the current element.
- We then update `max_so_far` to be the greater value between `max_so_far` and `max_ending_here`.
- Finally, the function returns the greater value between `max_so_far` and 0 to ensure non-negative results.

## Key Concepts

- **Kadane’s Algorithm**: An efficient algorithm to find the maximum sum contiguous subarray in linear time. This algorithm is based on dynamic programming.
- **std::max**: A C++ utility from the `<algorithm>` header used to find the maximum of two values.
- **Range-based for loop**: A modern C++ feature that allows easy iteration over containers like `std::vector`.

## Tags

- `#std/vector`
- `#std/algorithm`
- `#Kadane's-Algorithm`
- `#dynamic-programming`
---