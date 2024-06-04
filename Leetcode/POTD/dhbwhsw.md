# Intuition
The problem is to find the length of the longest palindrome that can be built with the letters from a given string. A palindrome reads the same backward as forward. The key insight is that for each character, if it appears an even number of times, it can fully contribute to the palindrome. If it appears an odd number of times, all but one of those characters can pair up to contribute to the palindrome, and one can be used in the middle if needed.

# Approach
1. Use a `HashSet` to track characters with odd occurrences.
2. Iterate through each character in the string:
   - If the character is already in the `HashSet`, it means we've encountered it an even number of times, so we remove it from the `HashSet` and increase the count by 2 (since pairs contribute to the palindrome length).
   - If the character is not in the `HashSet`, add it to the `HashSet`.
3. After processing all characters, if the `HashSet` is not empty, it means there are characters with an odd count, so we can place one of those characters in the middle of the palindrome.
4. Return the count.

# Complexity
- Time complexity:
The time complexity is $$O(n)$$, where $$n$$ is the length of the string. This is because we iterate through each character in the string once.

- Space complexity:
The space complexity is $$O(n)$$ in the worst case, where all characters are unique and added to the `HashSet`.

# Code
```java
class Solution {
    public int longestPalindrome(String s) {
        HashSet<Character> H = new HashSet<>();
        int count = 0;
        for (char c : s.toCharArray()) {
            if (H.contains(c)) {
                H.remove(c);
                count += 2;
            } else {
                H.add(c);
            }
        }
        if (!H.isEmpty()) {
            count += 1;
        }
        return count;
    }
}
