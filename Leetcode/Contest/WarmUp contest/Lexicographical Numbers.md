# Intuition
The intuition behind this solution is to generate all the integers from 1 to n in lexicographical order.

# Approach
1. Create an array of strings `A` to store the numbers as strings.
2. Fill the array with numbers converted to strings.
3. Sort the array of strings lexicographically.
4. Convert the sorted array of strings back to a list of integers using the `map` operation and `toList()` method.

# Complexity
- Time complexity: O(n log n)
  - Sorting the array of strings takes O(n log n) time.
  - Converting the sorted array of strings to a list of integers takes O(n) time.
  - Overall, the time complexity is dominated by the sorting step.
  
- Space complexity: O(n)
  - Additional space is used to store the array of strings and the resulting list of integers.

# Code
```java
import java.util.*;

class Solution {
    public List<Integer> lexicalOrder(int n) {
        String[] A = new String[n];
        for (int i = 0; i < n; i++) {
            A[i] = i + 1 + "";
        }
        Arrays.sort(A);
        List<Integer> B = Arrays.stream(A)
                                 .map((x) -> Integer.parseInt(x))
                                 .toList();
        return B;
    }
}
