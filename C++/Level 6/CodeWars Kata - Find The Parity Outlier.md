## CodeWars Kata - Find The Parity Outlier

[Link to the kata](https://www.codewars.com/kata/5526fc09a1bbd946250002dc/train/cpp)

### Problem Statement

You are given an array (which will have a length of at least 3, but could be very large) containing integers. The array is either entirely comprised of odd integers or entirely comprised of even integers except for a single integer N. Write a method that takes the array as an argument and returns this "outlier" N.

Examples:

- Given `[2, 4, 0, 100, 4, 11, 2602, 36]`, the result should be `11` (the only odd number).
  
- Given `[160, 3, 1719, 19, 11, 13, -21]`, the result should be `160` (the only even number).

### Solution

**Code**:
```cpp
#include <vector>
#include <algorithm>

int FindOutlier(std::vector<int> arr)
{
    auto isEven = [](int n) { return n % 2 == 0; };
    int evensInFirstThree = std::count_if(arr.begin(), arr.begin() + 3, isEven);

    if (evensInFirstThree >= 2) {
        return *std::find_if(arr.begin(), arr.end(), [isEven](int n) { return !isEven(n); });
    } else {
        return *std::find_if(arr.begin(), arr.end(), isEven);
    }
}
```

**Explanation**:

The solution starts by checking the parity (even/odd nature) of the first three numbers of the array. This helps in determining the overall nature of the array. If at least two of the first three numbers are even, the array is predominantly even, and the outlier will be odd. Conversely, if fewer than two of the first three are even, the array is predominantly odd, and the outlier will be even.

- `std::count_if` is utilized to count how many of the first three numbers are even.
- `std::find_if` is then used to find the outlier based on the information obtained from the initial check.

### Key Concepts

- `std::count_if`: This STL algorithm counts elements in a range that satisfy a given predicate.
  
- `std::find_if`: An algorithm that returns an iterator to the first element in the range for which a predicate returns true.

- Lambda functions: Used here for concise conditional checks (to determine if a number is even).

### Tags

- `#std/algorithm`
- `#std/vector`
- `#lambda-functions`
- `#conditional-checks`

---