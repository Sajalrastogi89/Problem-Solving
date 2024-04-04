# Approach
The problem requires finding the sum of all possible substrings of the given string. We can solve this efficiently using a mathematical approach without actually generating all substrings. We iterate through the string and calculate the contribution of each digit to all substrings.

# Explanation
1. Initialize `ans` to store the final result, `prev` to keep track of the sum so far, and `mod` for modular arithmetic.
2. Iterate through the string `s`.
3. For each character `s[i]`, calculate `curr`, the contribution of the current digit to all substrings.
4. Update `prev` with the current value of `curr`.
5. Update `ans` by adding `curr` to it.
6. Return `ans` as the result.

# Complexity
- Time complexity: O(n) where n is the length of the input string `s`. We traverse the string once.
- Space complexity: O(1). We only use a few variables to store the current and previous values.

# Code
```java
class Solution {
    // Function to find sum of all possible substrings of the given string.
    public static long sumSubstrings(String s) {
        long ans = 0, prev = 0, mod = 1000000007;
        for (int i = 0; i < s.length(); i++) {
            long curr = (prev * 10) % mod + (s.charAt(i) - '0') * (i + 1) % mod;
            prev = curr;
            ans = (ans + curr) % mod;
        }
        return ans;
    }
}
