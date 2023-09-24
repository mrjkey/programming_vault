## CodeWars Kata - Digital Root

[Link to the kata](https://www.codewars.com/kata/541c8630095125aba6000c00/train/cpp)

### Problem Statement

Digital root is the recursive sum of all the digits in a number. Given `n`, take the sum of the digits of `n`. If that value has more than one digit, continue reducing in this way until a single-digit number is produced. The input will be a non-negative integer.

### Solution

```cpp
int digital_root(int n)
{
    while (n > 9) {  // Continue until we have a single-digit number
        int sum = 0;
        while (n) {  // While n is not 0
            sum += n % 10;  // Add last digit of n to the sum
            n /= 10;  // Remove last digit from n
        }
        n = sum;  // Set n as sum for the next iteration (if needed)
    }
    return n;
}
```

**Explanation**: The solution focuses on iteratively summing up the digits of the number `n`. If the sum exceeds a single digit, the process is repeated until a single-digit number is achieved. We use modulo operation (`% 10`) to extract the least significant digit and integer division (`/= 10`) to remove the least significant digit. The `while` loop ensures this process is executed for every digit.

### Key Concepts

- **Modulo Operation**: It returns the remainder after division. `n % 10` will return the last digit of the number `n`.
- **Integer Division**: It returns the quotient after division. `n /= 10` will remove the last digit from the number `n`.

### Tags

- `#integer`
- `#iteration`
- `#modulo`
- `#division`

---