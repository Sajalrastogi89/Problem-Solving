# Intuition
The intuition behind swapping nibbles of an 8-bit integer is to convert the integer to its binary representation, divide the binary string into two parts (nibbles), and then swap these two parts.

# Approach
1. **Binary Conversion**: Convert the input integer `n` to its binary representation.
2. **Nibble Swapping**: Extract the upper and lower nibbles of the binary string and swap their positions.
3. **Binary to Integer Conversion**: Convert the swapped binary string back to an integer.

# Complexity
- Time complexity: \(O(1)\)
  - The time complexity is constant because the size of the input (an 8-bit integer) remains fixed regardless of the input value.
- Space complexity: \(O(1)\)
  - The space complexity is also constant because we only use a fixed amount of extra space to store the binary string and the result.

# Code
```java
class Solution {
    static int swapNibbles(int n) {
        String s = String.format("%8s", Integer.toBinaryString(n)).replace(' ', '0');
        String m = s.substring(4) + s.substring(0, 4);
        return Integer.parseInt(m, 2);
    }
}
