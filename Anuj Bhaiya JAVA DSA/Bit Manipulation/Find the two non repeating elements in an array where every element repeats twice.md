# Intuition
The intuition behind this approach is to use bitwise XOR to find the unique pair of elements in the array.

# Approach
1. Perform a bitwise XOR of all elements in the array to find the XOR of the two unique numbers.
2. Find the rightmost set bit (setBit) in the XOR result, which separates the two unique numbers.
3. Iterate through the array again:
   - For each element, check if the setBit is set or not.
   - If the setBit is set, XOR it with one variable (a), otherwise XOR it with another variable (b).
4. At the end of the iteration, 'a' will contain one unique number, and 'b' will contain the other unique number.

# Complexity
- Time complexity:
  The time complexity of this approach is O(n), where n is the number of elements in the array. We iterate through the array twice, and each iteration takes O(n) time.
  
- Space complexity:
  The space complexity is O(1) because we use only a constant amount of extra space.

# Code
```java
public class Main {
    public static void main(String[] args) {
        int[] A = {1, 1, 2, 2, 3, 4, 5, 5, 6, 6};
        int x = 0;
        for (int i : A) {
            x = x ^ i;
        }
        int j = 0;
        while (x > 0) {
            if ((x & 1) == 1) {
                break;
            }
            x = x >> 1;
            j++;
        }
        int a = 0, b = 0;
        for (int i : A) {
            if (((1 << j) & i) == 1) {
                a ^= i;
            } else {
                b ^= i;
            }
        }
        System.out.println(a + " " + b);
    }
}
