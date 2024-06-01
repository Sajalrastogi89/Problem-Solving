# OddEven Character Frequency

## Problem Statement
Given a string `s`, determine if the count of characters that meet certain conditions is even or odd. Specifically, for each character in the string:
- If the frequency of the character is even and its position in the alphabet is even, or
- If the frequency of the character is odd and its position in the alphabet is odd,
count it.

If the total count of such characters is even, return "EVEN". Otherwise, return "ODD".

## Intuition
To solve this problem, we need to:
1. Count the frequency of each character in the string.
2. Check the frequency and the alphabetical position of each character.
3. Based on the conditions, determine if the count is even or odd.

## Approach
1. Use a `HashMap` to count the frequency of each character in the string.
2. Iterate through the characters and check the conditions:
   - The character's frequency is even and its position in the alphabet is even.
   - The character's frequency is odd and its position in the alphabet is odd.
3. Count the number of characters that meet the conditions.
4. If the count is even, return "EVEN". Otherwise, return "ODD".

## Complexity
- **Time complexity**: \(O(n)\), where `n` is the length of the string. We iterate through the string twice.
- **Space complexity**: \(O(k)\), where `k` is the number of distinct characters in the string. This is for storing the frequency counts in the `HashMap`.

## Code
```java
import java.util.HashMap;

class Solution {
    public static String oddEven(String s) {
        HashMap<Character, Integer> H = new HashMap<>();
        for (char i : s.toCharArray()) {
            H.put(i, H.getOrDefault(i, 0) + 1);
        }
        int x = 0;
        for (char c : H.keySet()) {
            if ((((H.get(c) & 1) == 0) && (((c - 'a') + 1) & 1) == 0) || 
                (((H.get(c) & 1) != 0) && (((c - 'a') + 1) & 1) != 0)) {
                x++;
            }
        }
        if ((x & 1) == 0) {
            return "EVEN";
        } else {
            return "ODD";
        }
    }
}
