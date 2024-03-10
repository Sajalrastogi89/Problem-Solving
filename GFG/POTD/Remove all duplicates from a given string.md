# Intuition
The intuition behind this approach is to use a HashSet to keep track of unique characters encountered while iterating through the input string. If a character is encountered for the first time, it is added to the result string. If it's encountered again, it's skipped to avoid duplicates.

# Approach
1. Create an empty HashSet to store unique characters.
2. Iterate through the input string character by character.
3. For each character, check if it exists in the HashSet. If it does, skip it; otherwise, add it to the result string and the HashSet.
4. Finally, return the result string with duplicates removed.

# Complexity
- Time complexity: O(n), where n is the length of the input string. The algorithm iterates through the string once.
- Space complexity: O(k), where k is the number of unique characters in the input string. The space used by the HashSet will depend on the number of unique characters in the input string.

# Code
```java
import java.util.HashSet;

class Solution {
    String removeDuplicates(String str) {
        HashSet<Character> H = new HashSet<>();
        String ans = "";
        for (int i = 0; i < str.length(); i++) {
            if (H.contains(str.charAt(i)))
                continue;
            ans += str.charAt(i);
            H.add(str.charAt(i));
        }
        return ans;
    }
}
