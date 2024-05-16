# ZigZag Array

## Problem Statement
Given an array `arr[]` of length \( n \), the task is to rearrange the elements of the array such that every alternate element is greater than its adjacent elements.

## Approach
1. **Swap Elements**:
   - Implement a function `swap()` to swap two elements in the array.
2. **ZigZag Rearrangement**:
   - Iterate through the array from index \( 0 \) to \( n-2 \).
   - If the current element is less than the next element and the index is odd, or if the current element is greater than the next element and the index is even, swap the elements to make the array zigzag.
3. **Result**:
   - After the rearrangement, the array will have a zigzag pattern.

## Complexity
- **Time Complexity**: \( O(n) \), where \( n \) is the length of the input array.
  - The algorithm involves iterating through the array once.
- **Space Complexity**: \( O(1) \), as the algorithm uses only a constant amount of extra space.

## Code
```java
class Solution {
    public static void swap(int[] A, int i) {
        int temp = A[i];
        A[i] = A[i + 1];
        A[i + 1] = temp;
    }

    public static void zigZag(int n, int[] arr) {
        for (int i = 0; i < n - 1; i++) {
            if (arr[i] < arr[i + 1] && (i & 1) != 0) {
                swap(arr, i);
            }
            if (arr[i] > arr[i + 1] && (i & 1) == 0) {
                swap(arr, i);
            }
        }
    }
}
