
---

### CodeWars Kata - High and Low

[Link for Kata](https://www.codewars.com/kata/554b4ac871d6813a03000035/train/cpp)

#### Problem Statement

In this kata, you are given a string of space-separated numbers, and have to return the highest and lowest number.

**Examples**:

- `highAndLow("1 2 3 4 5")` returns "5 1"
- `highAndLow("1 2 -3 4 5")` returns "5 -3"
- `highAndLow("1 9 3 4 -5")` returns "9 -5"

**Notes**:

- All numbers are valid Int32, no need to validate them.
- There will always be at least one number in the input string.
- Output string must be two numbers separated by a single space, with the highest number first.

#### Solution

**Code**:

```cpp
#include <string>
#include <sstream>
#include <algorithm>

std::string highAndLow(const std::string& numbers){
    std::istringstream ss(numbers);  
    std::vector<int> numVector(std::istream_iterator<int>(ss), {});
    auto [minIt, maxIt] = std::minmax_element(numVector.begin(), numVector.end());
    return std::to_string(*maxIt) + " " + std::to_string(*minIt);
}
```

**Explanation**:

The solution leverages a single-pass algorithm (`std::minmax_element`) to determine the smallest and largest numbers from a vector of integers. The integers are directly inserted into the vector by parsing the input string using `std::istream_iterator<int>` and `std::istringstream`.

Structured bindings (`auto [minIt, maxIt]`) from C++17 provide a convenient way to extract the results from the `std::minmax_element` function.

#### Key Concepts

- `std::istringstream` - It's a stream class to operate on strings. It provides a way to extract values from strings.
  
- `std::istream_iterator<int>` - An input iterator that reads integers from a stream. It can be used to directly parse and insert elements into containers.

- `std::minmax_element` - An STL algorithm that returns a pair of iterators pointing to the smallest and largest elements in a range.

- Structured Bindings - A feature from C++17 allowing for easy unpacking of pairs or tuples. It enhances code readability.

#### Tags

- `#std/vector`
- `#std/istringstream`
- `#std/istream_iterator`
- `#algorithm/minmax_element`
- `#C++17/StructuredBindings`
- `#std/string`
- `#parsing`

---

## My bad code

```c++
#include <string>

std::string highAndLow(const std::string& numbers){
  int count = 0;
  int min, max;
  
  std::stringstream ss(numbers);
  int num;
  while(ss >> num){
    if(count == 0){
      min = num;
      max = num;
      count++;
    }else{
      if(num < min){
        min = num;
      }
      if(num > max){
        max = num;
      }
    }
  }
  
//   std::stringstream result;
//   result << std::to_string(max) << " " << std::to_string;
  return std::to_string(max) + " " + std::to_string(min);
  //your code here
}
```