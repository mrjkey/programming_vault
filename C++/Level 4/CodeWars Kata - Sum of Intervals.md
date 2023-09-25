## CodeWars Kata - Sum of Intervals

[Placeholder for Link to the kata](https://www.codewars.com/kata/52b7ed099cdc285c300001cd/train/cpp)

### Problem Statement

Write a function called `sumIntervals/sum_intervals` that accepts an array of intervals, and returns the sum of all the interval lengths. Overlapping intervals should only be counted once. 

Intervals are represented by a pair of integers in the form of an array. The first value of the interval will always be less than the second value. Interval example: `[1, 5]` is an interval from 1 to 5. The length of this interval is 4.

### Solution

**Code**:

```cpp
#include <vector>
#include <utility>
#include <algorithm>

int sum_intervals(std::vector<std::pair<int, int>> intervals) {
    std::sort(intervals.begin(), intervals.end(), [](const auto& a, const auto& b) {
        return a.first < b.first;
    });

    int sum = 0;
    int current_start = intervals[0].first;
    int current_end = intervals[0].second;

    for (const auto& interval : intervals) {
        if (interval.first <= current_end) {
            current_end = std::max(current_end, interval.second);
        } else {
            sum += current_end - current_start;
            current_start = interval.first;
            current_end = interval.second;
        }
    }

    sum += current_end - current_start;

    return sum;
}
```

**Explanation**:

1. Sort the intervals based on their start values.
2. Initialize variables to keep track of the current interval (`current_start` and `current_end`).
3. Loop through the intervals. If an interval starts before the current one ends, merge them. Otherwise, add the length of the current interval to the sum and update `current_start` and `current_end` with the new interval.
4. After the loop, add the length of the last interval to the sum.

### Key Concepts

- `std::sort`: Part of the `<algorithm>` header. Used to sort the elements in a range based on a certain condition.
- `std::max`: Returns the greater of two values. Used here to determine the end of a merged interval.
- Lambda functions: A concise way to define simple functions on the fly. Used here as a comparator for sorting.
  
### Tags

- `#std/vector`
- `#std/pair`
- `#std/algorithm`
- `#Lambda`
- `#Interval_Merging`

---

## Alternate Solution

```c++
#include <vector>
#include <utility>

int sum_intervals(std::vector<std::pair<int, int>> interavls) {
  sort(interavls.begin(), interavls.end());
  int ret = 0;
  int max_right = interavls[0].first;
  for (auto &i : interavls)
       if (i.second >= max_right) {
           ret += i.second - std::max(max_right, i.first);
           max_right = i.second;
       }
  return ret;
}
```
