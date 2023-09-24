# CodeWars Kata - Shufflings

[Link to the kata](https://www.codewars.com/kata/5254ca2719453dcc0b00027d/train/cpp)

## Problem Statement

In this kata, your task is to create all permutations of a non-empty input string and remove duplicates, if present.

Examples:

- With input 'a': Your function should return: ['a']
  
- With input 'ab': Your function should return ['ab', 'ba']
  
- With input 'abc': Your function should return ['abc','acb','bac','bca','cab','cba']

- With input 'aabb': Your function should return ['aabb', 'abab', 'abba', 'baab', 'baba', 'bbaa']
  
Note: The order of the permutations doesn't matter.

## Solution

**Code**:
```cpp
#include <string>
#include <vector>
#include <algorithm>
#include <set>

std::vector<std::string> permutations(std::string s) {
    std::set<std::string> resultSet;
    std::sort(s.begin(), s.end());
    do {
        resultSet.insert(s);
    } while(std::next_permutation(s.begin(), s.end()));
    
    return std::vector<std::string>(resultSet.begin(), resultSet.end());
}
```

**Explanation**:
1. We first sort the input string to get its smallest lexicographical permutation.
2. Using a `do-while` loop, we insert each permutation into a `std::set` to handle duplicates automatically and keep the values sorted.
3. `std::next_permutation` is used inside the loop to generate the next permutation until all permutations are exhausted.
4. Finally, the unique permutations from the `std::set` are transferred to a `std::vector` and returned.

## Key Concepts

- **std::sort**: Sorts elements in a range. It's used to get the string to its smallest permutation.

- **std::next_permutation**: Generates the next lexicographically greater permutation of a range. This is central to generating all permutations.

- **std::set**: A container that stores unique values in a sorted manner. We utilize this to handle duplicates and keep the permutations sorted.

## Tags

- #std/sort  [std::sort](https://cplusplus.com/reference/algorithm/sort/)
- #std/next_permutation [std::next_permutation](https://cplusplus.com/reference/algorithm/next_permutation/)
- #std/set[std::set](https://cplusplus.com/reference/set/set/)
- #algorithm/permutation
- #data-structure/vector [std::vector](https://cplusplus.com/reference/vector/vector/)

