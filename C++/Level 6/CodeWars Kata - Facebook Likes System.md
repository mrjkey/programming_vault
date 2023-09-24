# CodeWars Kata - Facebook Likes System

[Link Placeholder to Kata](https://www.codewars.com/kata/5266876b8f4bf2da9b000362/train/cpp)

## Problem Statement

You are tasked with creating a "like" system similar to Facebook. Implement the function which takes an array containing the names of people that like an item. The function must return the display text in the following formats:

- [] -> "no one likes this"
- ["Peter"] -> "Peter likes this"
- ["Jacob", "Alex"] -> "Jacob and Alex like this"
- ["Max", "John", "Mark"] -> "Max, John and Mark like this"
- ["Alex", "Jacob", "Mark", "Max"] -> "Alex, Jacob and 2 others like this"

For 4 or more names, the number in "and 2 others" simply increases.

## Solution

```cpp
#include <string>
#include <vector>

std::string likes(const std::vector<std::string> &names)
{
    size_t n = names.size();

    switch (n)
    {
        case 0: 
            return "no one likes this";
        case 1: 
            return names[0] + " likes this";
        case 2: 
            return names[0] + " and " + names[1] + " like this";
        case 3: 
            return names[0] + ", " + names[1] + " and " + names[2] + " like this";
        default: 
            return names[0] + ", " + names[1] + " and " + std::to_string(n - 2) + " others like this";
    }
}
```

**Explanation**:
The solution utilizes a `switch` statement to branch logic based on the number of names in the provided vector. Depending on the number of names, the appropriate string is constructed and returned.

## Key Concepts

- `std::vector`: A sequence container representing arrays that can change in size.
- `size()`: A member function of `std::vector` that returns the number of elements.
- `std::to_string()`: A function that converts numeric types to their string representation.

## Tags

- #std/vector
- #std/string
- #switch-statement

---