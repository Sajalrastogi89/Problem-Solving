# Problem: Count Number of Consecutive Ones

## Problem Statement
Given an integer \( n \), find the number of sequences of length \( n \) that consist only of 0s and 1s, such that there are no three consecutive 1s.

## Approach
The problem can be solved using dynamic programming. We maintain two arrays, \( A \) and \( B \), where:
- \( A[i] \) represents the number of valid sequences of length \( i \) that end with "11".
- \( B[i] \) represents the number of valid sequences of length \( i \) that end with "01" or "10".

### Algorithm:
1. **Base Case**: If \( n \) is 2, return 1 immediately because there is exactly one sequence of length 2 that ends with two consecutive ones: "11".
2. **Initialization**:
   - Initialize \( \text{mod} = 10^9 + 7 \) to prevent overflow.
   - Initialize arrays \( A \) and \( B \) of size \( n + 1 \) to store intermediate results.
   - Set \( A[2] = 1 \) and \( B[1] = 0 \) as base cases.
3. **Dynamic Programming Transition**:
   - For \( i = 3 \) to \( n \), update \( B[i] \) and \( A[i] \) using the following recurrence relations:
     - \( B[i] = (B[i - 1] + B[i - 2]) \% \text{mod} \)
     - \( A[i] = ((A[i - 1] \times 2) \% \text{mod} + B[i]) \% \text{mod} \)
4. **Final Result**: Return \( A[n] \% \text{mod} \), which represents the number of valid sequences of length \( n \) that end with "11".

## Complexity Analysis
- **Time Complexity**: \( O(n) \)
- **Space Complexity**: \( O(n) \)

## Code
```java
class Solution {
    static int numberOfConsecutiveOnes(int n) {
        if (n == 2)
            return 1;
        int mod = 1000000007;
        int[] A = new int[n + 1];
        int[] B = new int[n + 1];
        A[2] = 1;
        B[1] = 0;
        B[2] = 1;
        for (int i = 3; i <= n; i++) {
            B[i] = (B[i - 1] + B[i - 2]) % mod;
            A[i] = ((A[i - 1] * 2) % mod + B[i]) % mod;
        }
        return A[n] % mod;
    }
}
