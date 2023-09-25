# CodeWars Kata - Range Extraction

[Link to Kata](https://www.codewars.com/kata/51ba717bb08c1cd60f00002f/train/cpp)

## Problem Statement
A format for expressing an ordered list of integers is to use a comma-separated list of either individual integers or a range of integers denoted by the starting integer separated from the end integer in the range by a dash, '-'. The range includes all integers in the interval including both endpoints. It is not considered a range unless it spans at least 3 numbers. The task is to take a list of integers in increasing order and return a correctly formatted string in the range format.

Example:

Input: `{-10, -9, -8, -6, -3, -2, -1, 0, 1, 3, 4, 5, 7, 8, 9, 10, 11, 14, 15, 17, 18, 19, 20}`

Output: `"-10--8,-6,-3-1,3-5,7-11,14,15,17-20"`

## Solution

### Code:
```cpp
#include <string>
#include <vector>
#include <sstream>  
#include <algorithm> 

std::string range_extraction(std::vector<int> args) {
    std::ostringstream oss;
    for (auto it = args.begin(); it != args.end(); ) {
        auto range_start = it;
        auto range_end = std::adjacent_find(it, args.end(), [](int a, int b) { return b - a != 1; });

        if (range_end == args.end() || std::next(range_end) == args.end()) {
            range_end = args.end();
        } else {
            range_end = std::next(range_end);
        }

        if (std::distance(range_start, range_end) > 2) {
            oss << *range_start << "-" << *(range_end - 1);
        } else {
            while (range_start != range_end) {
                oss << *range_start;
                if (std::next(range_start) != range_end) {
                    oss << ",";
                }
                ++range_start;
            }
        }

        it = range_end;
        if (it != args.end()) {
            oss << ",";
        }
    }
    return oss.str();
}
```

### Explanation:
The solution processes the input vector in a single pass, efficiently identifying ranges and individual numbers. It uses the `std::adjacent_find` function to search for the end of a contiguous range of numbers and then uses the `std::ostringstream` to build the result string dynamically. The `std::next` and `std::distance` functions are used to help with iterator manipulation.

## Key Concepts:

- `std::adjacent_find`: Returns the first iterator where adjacent elements meet a certain condition. Useful for identifying the end of a contiguous range.
  
- `std::ostringstream`: A stream-based container for building strings dynamically. It provides a performance advantage over frequent concatenations with `std::string`.
  
- `std::next`: Advances the iterator by a given number (default is 1). Useful for iterator manipulation.
  
- `std::distance`: Gives the number of items between two iterators. Used to determine the size of the identified range.

## Tags:
- `#std/vector`
- `#std/ostringstream`
- `#std/algorithm`
- `#iterators`
- `#std/adjacent_find`
- `#lambda-functions`
---

Copy and paste the above content directly into an Obsidian note or any markdown editor for the desired formatting.


## Alternate Solution

```c++
#include <string>
#include <set>

std::string range_extraction(std::vector<int> args)
{
    using Range = std::pair<int, int>;
    std::vector<Range> ranges;
    for(auto &i : args)
        if(ranges.empty() || ranges.back().second + 1 != i)
            ranges.push_back({i, i});
        else
            ++ranges.back().second;

    std::string result;
    for(auto &r : ranges)
        if(r.first == r.second)
            result.append(std::to_string(r.first) + ",");
        else
            result.append(std::to_string(r.first) +
                          ((r.first + 1 == r.second) ? ',' : '-') +
                          std::to_string(r.second) +
                          ",");
    result.pop_back();
    return result;
}
```


