# Intuition
The problem seems to involve searching for occurrences of a pattern string within a text string. The approach likely involves iterating through the text string and checking for matches with the pattern string.

# Approach
The provided code defines a `Solution` class with two methods:
1. `func(int i, String p, String t)`: This method checks if a pattern string `p` occurs at a specific index `i` within a text string `t`. It iterates through the characters of both `p` and `t`, starting from index `i`, and checks for matches.
2. `search(String p, String t)`: This method searches for occurrences of a pattern string `p` within a text string `t`. It iterates through the characters of `t` and calls the `func` method to check for matches with `p`.

# Complexity
- Time complexity:
  - The time complexity of the `func` method is O(n), where n is the length of the pattern string `p` or the remaining length of the text string `t`, whichever is smaller. The time complexity of the `search` method depends on the length of the text string `t` and the number of occurrences of the pattern string `p`.
- Space complexity:
  - The space complexity is O(1) for both methods as they use only a constant amount of extra space, regardless of the input size.

# Code
```java
class Solution {
    boolean func(int i, String p, String t) {
        int j = 0;
        for (j = 0; j < p.length() && i < t.length(); j++) {
            if (p.charAt(j) != t.charAt(i++))
                return false;
        }
        return j == p.length();
    }

    ArrayList<Integer> search(String p, String t) {
        ArrayList<Integer> A = new ArrayList<>();
        for (int i = 0; i < t.length(); i++) {
            if (t.charAt(i) == p.charAt(0)) {
                if (func(i, p, t)) {
                    A.add(i + 1);
                }
            }
        }
        return A;
    }
}
