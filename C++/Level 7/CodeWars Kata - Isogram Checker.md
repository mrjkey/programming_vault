## CodeWars Kata - Isogram Checker

[Link to the Kata](https://www.codewars.com/kata/54ba84be607a92aa900000f1/train/cpp)

### Problem Statement

An isogram is a word that has no repeating letters, consecutive or non-consecutive. Implement a function that determines whether a string that contains only letters is an isogram. Assume the empty string is an isogram. Ignore letter case.

Example:

- "Dermatoglyphics" --> true
- "aba" --> false
- "moOse" --> false (ignore letter case)

### Solution

```cpp
#include <string>
#include <set>
#include <algorithm>
#include <cctype>

bool is_isogram(std::string str) {
    // Convert the string to lowercase to make the comparison case-insensitive
    std::transform(str.begin(), str.end(), str.begin(), [](unsigned char c){ return std::tolower(c); });

    // Use std::set for deduplication 
    std::set<char> char_set(str.begin(), str.end());

    // If the sizes are the same, it's an isogram. Otherwise, there's a duplicate character.
    return char_set.size() == str.size();
}
```

**Explanation**:

- The `std::transform` function is used to convert every character in the string `str` to its lowercase equivalent. This ensures the solution is case-insensitive.
- An `std::set` named `char_set` is then constructed using the characters from the string `str`. Since `std::set` only stores unique elements, any duplicate characters will be automatically discarded.
- The solution checks if the size of `char_set` is equal to the size of the string `str`. If they're equal, it means there were no duplicate characters in `str` and the function returns `true`. If they're not equal, it means there were duplicate characters and the function returns `false`.

### Key Concepts

- `std::transform`: A standard algorithm to apply a given function to a range of elements.
- `std::tolower`: Converts a character to its lowercase representation.
- `std::set`: A container that contains a sorted set of unique elements.

### Tags

#std/transform #std/tolower #std/set

---