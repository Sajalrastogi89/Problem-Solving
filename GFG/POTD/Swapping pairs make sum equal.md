# Find Swap Values

## Problem Statement
Given two arrays `a[]` and `b[]` of lengths \( n \) and \( m \) respectively, the task is to determine if there exists a pair of values `x` and `y` such that after swapping `x` from array `a[]` and `y` from array `b[]`, the sums of both arrays become equal. If such a pair exists, return `1`; otherwise, return `-1`.

## Approach
1. **Calculate Sums**: Calculate the sum of elements in both arrays `a[]` and `b[]`.
2. **Find Difference**: Calculate the difference between the sums of array `a[]` and array `b[]`. If the difference is odd, it's impossible to make the sums equal, so return `-1`.
3. **Calculate Target Difference**: Determine the target difference required for the sums of both arrays to become equal. This is half of the difference calculated in the previous step.
4. **HashSet**: Create a HashSet from array `b[]` to efficiently check if a value exists in the array.
5. **Iterate and Check**: Iterate through each element in array `a[]`. For each element `x`, calculate the corresponding element `y` such that swapping `x` from array `a[]` with `y` from array `b[]` would result in the sums becoming equal. Check if `y` exists in the HashSet. If found, return `1`.
6. **Return Result**: If no such pair exists, return `-1`.

## Complexity
- **Time Complexity**: \( O(n + m) \), where \( n \) and \( m \) are the lengths of arrays `a[]` and `b[]` respectively. Calculating the sums of both arrays and creating the HashSet both take linear time.
- **Space Complexity**: \( O(m) \), for the HashSet used to store elements from array `b[]`.

## Code
```java
import java.util.HashSet;

class Solution {
    long findSwapValues(long a[], int n, long b[], int m) {
        long sumA = 0, sumB = 0;
        
        for (long num : a) {
            sumA += num;
        }
        for (long num : b) {
            sumB += num;
        }
        
        long diff = sumA - sumB;
        if (diff % 2 != 0) {
            return -1;
        }
        
        long targetDiff = diff / 2;
        
        HashSet<Long> setB = new HashSet<>();
        for (long num : b) {
            setB.add(num);
        }
        
        for (long x : a) {
            long y = x - targetDiff;
            if (setB.contains(y)) {
                return 1;
            }
        }
        
        return -1;
    }
}
