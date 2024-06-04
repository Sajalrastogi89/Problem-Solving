# Intuition
To find the next binary number for a given binary string, we can treat the string as a binary number and simulate the addition of 1. The process is similar to how we handle carry-over in decimal addition.

# Approach
1. Start from the rightmost bit of the binary string.
2. Traverse the string from right to left:
   - If the current bit is '1', change it to '0' and continue to the next bit (simulating carry-over).
   - If the current bit is '0', change it to '1' and stop as no further carry-over is needed.
3. If the leftmost bit also causes a carry-over (all bits are '1'), prepend '1' to the result.
4. Remove any leading zeros from the result.

# Complexity
- Time complexity:
The time complexity is $$O(n)$$, where $$n$$ is the length of the binary string. This is because we may need to traverse the entire string in the worst case (when all bits are '1').

- Space complexity:
The space complexity is $$O(n)$$ as we are creating a new string to store the result.

# Code
```java
class Solution {
    String binaryNextNumber(String s) {
        String ans = "";
        for (int i = s.length() - 1; i >= 0; i--) {
            if (s.charAt(i) == '1') {
                ans = "0" + ans;
                if (i == 0) {
                    return "1" + ans;
                }
            } else {
                ans = s.substring(0, i) + "1" + ans;
                break;
            }
        }
        ans = ans.replaceAll("^[0]*", "");
        return ans;
    }
}
