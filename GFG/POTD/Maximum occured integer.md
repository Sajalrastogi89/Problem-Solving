# Maximum Occurred Integer in Ranges

## Problem Statement
Given \( n \) ranges represented by two arrays `l[]` and `r[]` of length \( n \) each, and an integer `maxx`, the task is to find the maximum occurred integer in all ranges.

## Approach
1. **Counting Occurrences**:
   - Create an array `A[]` of size `maxx + 2` initialized to zeros.
   - Iterate through the given ranges and increment the count of `l[i]` and decrement the count of `r[i] + 1` in the array `A[]`.
2. **Prefix Sum**:
   - Compute the prefix sum of the array `A[]`.
3. **Find Maximum Occurred Integer**:
   - Iterate through the prefix sum array and find the maximum value and its corresponding index.
4. **Return Result**:
   - Return the index of the maximum value found.

## Complexity
- **Time Complexity**: \( O(n + maxx) \), where \( n \) is the number of ranges and `maxx` is the maximum value in the ranges.
  - Iterating through the ranges takes \( O(n) \) time.
  - Computing the prefix sum takes \( O(maxx) \) time.
- **Space Complexity**: \( O(maxx) \), for the array `A[]` used to store the counts.

## Code
```java
class Solution {
    // Function to find the maximum occurred integer in all ranges.
    public static int maxOccured(int n, int l[], int r[], int maxx) {
        int[] A = new int[maxx + 2];
        
        // Count occurrences in ranges
        for (int i = 0; i < n; i++) {
            A[l[i]] += 1;
            A[r[i] + 1] -= 1;
        }
        
        // Compute prefix sum
        for (int i = 1; i < maxx + 1; i++) {
            A[i] += A[i - 1];
        }
        
        // Find maximum occurred integer
        int ans = 0;
        int val = A[0];
        for (int i = 1; i < maxx + 2; i++) {
            if (A[i] > val) {
                val = A[i];
                ans = i;
            }
        }
        
        return ans;
    }
}
