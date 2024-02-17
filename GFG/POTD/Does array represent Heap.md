# Problem Statement
Given an array `a` of long integers and its length `n`, the task is to determine whether the elements of the array form a special type of sequence where each element is greater than its children in a binary tree.

# Intuition
The function `countSub` checks whether the elements of the given array form a special type of sequence as described in the problem statement.

# Approach
1. Iterate through the array up to half its length.
2. For each element at index `i`, compare it with its left child `2*(i+1)-1` and its right child `2*(i+1)`, if they exist.
3. If the current element is smaller than any of its children, return `false`.
4. If all elements pass the comparison, return `true`.

# Complexity
- Time complexity: O(n) where n is the length of the array.
- Space complexity: O(1).

# Code
```java
class Solution {
    
    public boolean countSub(long a[], long n)
    {
        for(int i = 0; i < n / 2; i++) {
            if (a[i] < a[2 * (i + 1) - 1] || (2 * (i + 1) < n && a[i] < a[2 * (i + 1)]))
                return false;
        }
        return true;
    }
}
