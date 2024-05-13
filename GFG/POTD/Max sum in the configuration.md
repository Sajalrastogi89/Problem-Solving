# Maximum Sum of i*arr[i]

## Problem Statement
Given an array `a[]` of length \( n \), the task is to find the maximum possible sum of `i*arr[i]` where `i` varies from \( 0 \) to \( n-1 \).

## Approach
1. **Initial Sum Calculation**: Calculate the initial sum `ansSum` and `arrSum`.
   - Initialize `ansSum` and `arrSum` to \( 0 \).
   - Iterate through the array `a[]` and calculate the sum of `i*arr[i]` and the sum of all elements of `a[]`.
2. **Max Sum Calculation**:
   - Initialize `ans` to `ansSum`.
   - Iterate through the array `a[]` from index \( 0 \) to \( n-2 \).
   - Update `ansSum` by subtracting `arrSum` and adding \( n \times a[i] \) for each iteration.
   - Update `ans` to the maximum of `ansSum` and the current value of `ans`.
3. **Return Result**: Return the final value of `ans`.

## Complexity
- **Time Complexity**: \( O(n) \), where \( n \) is the length of the input array `a[]`.
  - Calculating the initial sum and the maximum sum both require traversing the array once.
- **Space Complexity**: \( O(1) \), as the algorithm uses only a constant amount of extra space.

## Code
```java
class Solution {
    long max_sum(int a[], int n) {
        long ansSum = 0;
        long arrSum = 0;
        
        // Calculate initial sum
        for (int i = 0; i < n; i++) {
            ansSum += (long) a[i] * i;
            arrSum += a[i];
        }
        
        long ans = ansSum;
        
        // Iterate and calculate maximum sum
        for (int i = 0; i < n - 1; i++) {
            ansSum = ansSum - arrSum + ((long) n * a[i]);
            ans = Math.max(ansSum, ans);
        }
        
        return ans;
    }
}
