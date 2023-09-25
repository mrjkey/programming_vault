## CodeWars Kata - Snail Sort

[Placeholder Link to Kata](https://www.codewars.com/kata/521c2db8ddc89b9b7a0000c1/train/cpp)

---

### Problem Statement
Given an n x n array, return the array elements arranged from outermost elements to the middle element, traveling clockwise.

Example:
```
array = [[1,2,3],
         [4,5,6],
         [7,8,9]]
snail(array) #=> [1,2,3,6,9,8,7,4,5]
```
For better understanding, please follow the numbers of the next array consecutively:

```
array = [[1,2,3],
         [8,9,4],
         [7,6,5]]
snail(array) #=> [1,2,3,4,5,6,7,8,9]
```

The idea is not to sort the elements from the lowest value to the highest; the idea is to traverse the 2-d array in a clockwise snailshell pattern.

NOTE: The 0x0 (empty matrix) is represented as an empty array inside an array `[[]]`.

---

### Solution

**Code**:
```cpp
#include <vector>
#include <algorithm>

std::vector<int> snail(const std::vector<std::vector<int>> &snail_map) {
    std::vector<int> result;
    if(snail_map.empty() || snail_map[0].empty()) return result; // Check for empty matrix

    int top = 0, bottom = snail_map.size() - 1, left = 0, right = snail_map[0].size() - 1;

    while(top <= bottom && left <= right) {
        // Move right
        for(int i = left; i <= right; ++i) {
            result.push_back(snail_map[top][i]);
        }
        ++top;

        // Move down
        for(int i = top; i <= bottom; ++i) {
            result.push_back(snail_map[i][right]);
        }
        --right;

        // Move left
        if(top <= bottom) {
            for(int i = right; i >= left; --i) {
                result.push_back(snail_map[bottom][i]);
            }
            --bottom;
        }

        // Move up
        if(left <= right) {
            for(int i = bottom; i >= top; --i) {
                result.push_back(snail_map[i][left]);
            }
            ++left;
        }
    }

    return result;
}
```

**Explanation**:
- We have four variables `top`, `bottom`, `left`, and `right` which denote the current boundary of our matrix that hasn't been visited yet.
- We peel off the matrix layer by layer. In each layer, we move:
  1. Right across the top
  2. Down the right side
  3. Left across the bottom
  4. Up the left side
- After completing each step, we adjust the corresponding boundary variable (`top`, `right`, `bottom`, `left`) to move inwards.
- The condition in the middle of the loop checks if we still have more layers left to traverse.

---

### Key Concepts
- `std::vector`: A dynamic array that can grow in size.
- Looping structures: The primary logic relies on simple `for` loops to traverse the matrix in the desired pattern.

---

Tags: `#std/vector` `#loop` `#matrix`

---
