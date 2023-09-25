# CodeWars Kata - Mountainous Direction Reduction

[Placeholder Link to the Kata](https://www.codewars.com/kata/550f22f4d758534c1100025a/train/cpp)

## Problem Statement

Once upon a time, on a way through the old wild mountainous west, a man was given directions to go from one point to another. The directions were "NORTH", "SOUTH", "WEST", "EAST". Clearly "NORTH" and "SOUTH" are opposite, "WEST" and "EAST" too. The objective is to remove any opposite directions that are consecutive in the directions list, simplifying the man's journey.

Given a list of directions, the goal is to provide the man with a simplified plan by eliminating unnecessary opposite directions that appear consecutively.

## Solution

### Code

```cpp
#include <vector>
#include <string>
#include <stack>
#include <unordered_map>

class DirReduction
{
public:
    static std::vector<std::string> dirReduc(std::vector<std::string> &arr)
    {
        std::stack<std::string> stk;
        
        std::unordered_map<std::string, std::string> opposites = {
            {"NORTH", "SOUTH"},
            {"SOUTH", "NORTH"},
            {"EAST", "WEST"},
            {"WEST", "EAST"}
        };

        for (const auto &direction : arr)
        {
            if (!stk.empty() && stk.top() == opposites[direction])
                stk.pop();
            else
                stk.push(direction);  
        }

        std::vector<std::string> result;
        while (!stk.empty())
        {
            result.push_back(stk.top());
            stk.pop();
        }
        
        std::reverse(result.begin(), result.end());

        return result;
    }
};
```

### Explanation

- A `stack` named `stk` is utilized to track the directions.
- The `opposites` unordered_map provides an efficient way to determine the opposing direction of a given one.
- As we loop over the input `arr`, we check if the current direction is the opposite of the stack's top direction. If they are opposites, we pop the stack. Otherwise, the current direction is pushed onto the stack.
- After iterating through all directions, we convert the stack to a `vector` and then reverse it to obtain the final result.

## Key Concepts

- **std::stack**: A container adapter that provides last-in-first-out (LIFO) data structure.
- **std::unordered_map**: A hash table based associative container with unique keys.
- **std::reverse**: A function to reverse elements in a range.

## Tags

#std/vector #std/string #std/stack #std/unordered_map #algorithm/simplification

---