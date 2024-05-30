# Intuition
The intuition behind this solution is to count the occurrences of each character in the string using a HashMap. Then, iterate through the HashMap to find the index of the first unique character.

# Approach
1. Create a HashMap to store the count of occurrences of each character in the string.
2. Iterate through the string and update the count of each character in the HashMap.
3. Iterate through the keys of the HashMap and find the index of the first unique character by checking its count in the string.
4. Return the index of the first unique character if found, otherwise return -1.

# Complexity
- Time complexity: O(n)
  - Building the HashMap takes O(n) time.
  - Iterating through the HashMap to find the first unique character takes O(n) time.
  - Overall, the time complexity is O(n).
  
- Space complexity: O(n)
  - Additional space is used to store the HashMap.

# Code
```java
import java.util.*;

class Solution {
    public int firstUniqChar(String s) {
        int ans = Integer.MAX_VALUE;
        HashMap<Character, Integer> H = new HashMap<>();
        for (int i = 0; i < s.length(); i++) {
            H.put(s.charAt(i), H.getOrDefault(s.charAt(i), 0) + 1);
        }
        for (char i : H.keySet()) {
            if (H.get(i) == 1)
                ans = Math.min(ans, s.indexOf(i));
        }
        if (ans != Integer.MAX_VALUE)
            return ans;
        else
            return -1;
    }
}
