# Prefix Distinct Count Problem Solution

## Intuition
The problem can be solved by maintaining a HashSet to keep track of distinct elements encountered till each index in the input array.

## Approach
1. Create a HashSet to store distinct elements.
2. Initialize an integer array `ans` to store the count of distinct elements encountered till each index.
3. Iterate through the input array `arr`.
4. Add each element of `arr` to the HashSet.
5. Update the corresponding index in `ans` with the current size of the HashSet, which represents the count of distinct elements encountered till that index.
6. Return the `ans` array.

## Complexity
- Time complexity: O(n), where n is the length of the input array `arr`. We traverse the array once.
- Space complexity: O(n), where n is the length of the input array `arr`. We use extra space for the HashSet and the `ans` array.

## Code (Java)
```java
class Solution {
    public int[] prefixDistinct(int n, int arr[]) {
        HashSet<Integer> H = new HashSet<>();
        int[] ans = new int[n];
        for (int i = 0; i < n; i++) {
            H.add(arr[i]);
            ans[i] = H.size();
        }
        return ans;
    }
}
