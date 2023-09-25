# CodeWars Kata - Human-friendly Duration Format

[Placeholder Link](https://www.codewars.com/kata/52742f58faf5485cae000b9a/train/cpp)

## Problem Statement
Your task is to write a function which formats a duration, given as a number of seconds, in a human-friendly way. The function must accept a non-negative integer. If it is zero, it just returns "now". Otherwise, the duration is expressed as a combination of years, days, hours, minutes, and seconds.

For example:

- For `seconds = 62`, the function should return: "1 minute and 2 seconds".
- For `seconds = 3662`, the function should return: "1 hour, 1 minute and 2 seconds".

The function needs to adhere to specific rules including the proper use of plurals, component separation, and maximizing the use of each time unit.

## Solution

### Code

```cpp
#include <string>
#include <vector>
#include <tuple>

std::string format_duration(int seconds) {
    if (seconds == 0) return "now"; // Special case

    // Define the units of time and their respective lengths in seconds
    std::vector<std::tuple<int, std::string>> units = {
        {365*24*60*60, "year"},
        {24*60*60, "day"},
        {60*60, "hour"},
        {60, "minute"},
        {1, "second"}
    };

    std::vector<std::string> parts; // To store the formatted parts of the duration

    // Break the duration into its constituent parts
    for (const auto& [unit_seconds, unit_name] : units) {
        if (seconds >= unit_seconds) {
            int value = seconds / unit_seconds;
            seconds %= unit_seconds;
            parts.push_back(std::to_string(value) + " " + unit_name + (value > 1 ? "s" : ""));
        }
    }

    // Format the final string
    std::string result;
    for (size_t i = 0; i < parts.size(); ++i) {
        if (i > 0) {
            if (i == parts.size() - 1) // If it's the last element
                result += " and ";
            else
                result += ", ";
        }
        result += parts[i];
    }

    return result;
}
```

### Explanation

1. We initiate by checking if the given `seconds` equals 0 and handle the special case.
2. We then define the different time units along with their corresponding durations in seconds.
3. Next, we iterate over these units to break down the input duration (`seconds`) into its various components (years, days, hours, etc.), adding each to the `parts` vector.
4. Finally, we construct the result string, concatenating the components with either a comma or "and" based on their position in the `parts` vector.

## Key Concepts

- **Structured Bindings in C++**: Used to unpack the tuple into individual variables (`unit_seconds` and `unit_name`) for each iteration.
- **std::vector**: An STL container used to dynamically store multiple items. In this solution, it's used to store formatted time components.
- **std::tuple**: A template class that provides a way to store multiple data types in a single unit. Used here to map units of time to their string representations.

## Tags

#std/vector #std/tuple #structured-bindings #division #modulus

---