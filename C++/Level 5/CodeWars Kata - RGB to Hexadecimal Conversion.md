# CodeWars Kata - RGB to Hexadecimal Conversion

[Link to the kata](https://www.codewars.com/kata/513e08acc600c94f01000001/train/cpp)

## Problem Statement
Complete a function that takes in RGB decimal values and returns its hexadecimal representation. Valid decimal values for RGB are 0-255. Any values that fall out of that range must be rounded to the closest valid value. The answer should always be 6 characters long.

Examples:
- 255, 255, 255 -> "FFFFFF"
- 255, 255, 300 -> "FFFFFF"
- 0, 0, 0       -> "000000"
- 148, 0, 211   -> "9400D3"

## Solution

```cpp
#include <string>
#include <sstream>
#include <algorithm>
#include <iomanip>

class RGBToHex
{
public:
    static std::string rgb(int r, int g, int b)
    {
        r = std::clamp(r, 0, 255);
        g = std::clamp(g, 0, 255);
        b = std::clamp(b, 0, 255);

        std::stringstream ss;
        ss << std::hex << std::uppercase;
        ss << std::setw(2) << std::setfill('0') << r;
        ss << std::setw(2) << std::setfill('0') << g;
        ss << std::setw(2) << std::setfill('0') << b;

        return ss.str();
    }
};
```

### Explanation:
The solution leverages the `std::clamp` function to ensure RGB values are in the range [0,255]. Then, a `std::stringstream` is utilized to convert these clamped integer values into their hexadecimal representations. `std::setw` and `std::setfill` manipulators are employed to ensure two characters are output for each RGB value, even for values like 5 (resulting in "05").

## Key Concepts

- `std::clamp`: A function that constrains a value between two boundary values.
- `std::stringstream`: Allows stream operations on strings, making it easy to convert between strings and other data types.
- `std::setw` and `std::setfill`: Stream manipulators to set the width of the next input/output operation and the fill character used for padding, respectively.

## Tags

- #std/algorithm
- #std/string
- #std/stringstream
- #std/iomanip
- #std/hex
- #conversion


