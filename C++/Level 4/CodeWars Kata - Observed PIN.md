# CodeWars Kata - Observed PIN

[Link to the kata](https://www.codewars.com/kata/5263c6999e0f40dee200059d/train/cpp)

## Problem Statement
Given the observed PIN, compute all possible combinations of PINs considering the adjacent digits on a telephone keypad.

For example, for the digit '8', the adjacent digits include '5', '7', '8', '9', and '0'.

## Solution

### Code:
```cpp
#include <string>
#include <vector>
#include <unordered_map>

std::unordered_map<char, std::string> adjacent = {
    {'0', "08"},
    {'1', "124"},
    {'2', "1235"},
    {'3', "236"},
    {'4', "1457"},
    {'5', "24568"},
    {'6', "3569"},
    {'7', "478"},
    {'8', "57890"},
    {'9', "689"}
};

void generate_pins(const std::string& observed, std::string current, int index, std::vector<std::string>& results) {
    if (index == observed.size()) {
        results.push_back(current);
        return;
    }
    
    char key = observed[index];
    for (char ch : adjacent[key]) {
        generate_pins(observed, current + ch, index + 1, results);
    }
}

std::vector<std::string> get_pins(std::string observed) {
    std::vector<std::string> results;
    generate_pins(observed, "", 0, results);
    return results;
}
```

### Explanation:
- An unordered_map named `adjacent` is created to store the adjacent numbers for each digit on a phone keypad.
- `generate_pins` is a recursive function which generates all possible PINs based on the observed PIN and the adjacency list.
- If the current `index` is equal to the length of the observed PIN, the currently formed PIN is added to the results.
- Otherwise, for each adjacent digit of the currently observed digit, the function is recursively called.
- `get_pins` is a wrapper function that initializes the recursive call to `generate_pins` and returns the final list of possible PINs.

## Key Concepts

- **Recursion**: The method by which a function calls itself, used here to generate all possible combinations of PINs.
- **unordered_map**: A container that stores key-value pairs in no specific order.
  
## Tags
- #std/unordered_map
- #std/vector
- #std/string
- #recursion
```

You can copy-paste this markdown directly into Obsidian.