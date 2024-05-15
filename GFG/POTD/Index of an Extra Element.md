# Finding the Extra Element

## Problem Statement
Given two arrays `arr1[]` and `arr2[]` of lengths \( n \) and \( n-1 \) respectively, where `arr2[]` is a subset of `arr1[]`, the task is to find the index of the extra element present in `arr1[]` compared to `arr2[]`.

## Approach
1. **Counting Occurrences**:
   - Create a HashMap `map` to count the occurrences of elements in `arr2[]`.
2. **Find Extra Element**:
   - Iterate through the elements of `arr1[]`.
   - For each element, check if it exists in the HashMap `map`.
   - If an element is not found in `map`, return its index as it is the extra element in `arr1[]`.
3. **Return Result**:
   - If no extra element is found, return `-1`.

## Complexity
- **Time Complexity**: \( O(n) \), where \( n \) is the length of `arr1[]`.
  - Building the HashMap and iterating through `arr1[]` both take linear time.
- **Space Complexity**: \( O(n) \), for the HashMap `map` used to store elements from `arr2[]`.

## Code
```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    public int findExtra(int n, int arr1[], int arr2[]) {
        // Count occurrences of elements in arr2
        Map<Integer, Integer> map = new HashMap<>();
        for (int num : arr2) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }

        // Find the extra element in arr1
        for (int i = 0; i < arr1.length; i++) {
            if (!map.containsKey(arr1[i])) {
                return i; // Return the index of the extra element
            }
        }
        
        return -1;
    }
}
