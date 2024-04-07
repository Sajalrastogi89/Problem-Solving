# Minimum Jumps Problem Solution

## Intuition
The problem can be solved by maintaining a HashMap to store the positions of elements encountered in the array. By iterating through the array and updating the positions accordingly, we can find the minimum number of jumps required.

## Approach
1. Create a class `Pair` to represent a pair of values (`x` and `y`).
2. Define a `Solution` class with a static method `minJumps` that takes an integer `n` and an integer array `arr` as input and returns the minimum number of jumps required.
3. Create a HashMap `H` to store the positions of elements encountered in the array.
4. Iterate through the array `arr` and update the positions in the HashMap.
5. Calculate the maximum distance between any two occurrences of the same element in the HashMap, which represents the maximum number of jumps required to cover all occurrences of each element.
6. Subtract the maximum distance from the total number of elements to get the minimum number of jumps required.
7. Return the result.

## Complexity
- Time complexity: O(n), where n is the length of the input array `arr`. We traverse the array once to populate the HashMap.
- Space complexity: O(n), where n is the number of unique elements in the input array `arr`. We use extra space for the HashMap.

## Code (Java)
```java
class Pair<x, y> {
    x a;
    y b;
    
    Pair(x a, y b) {
        this.a = a;
        this.b = b;
    }
}

class Solution {
    public static int minJumps(int n, int[] arr) {
        HashMap<Integer, Pair<Integer, Integer>> H = new HashMap<>();
        
        for (int i = 0; i < n; i++) {
            if (H.containsKey(arr[i])) {
                H.put(arr[i], new Pair(H.get(arr[i]).a, i));
            } else {
                H.put(arr[i], new Pair(i, i));
            }
        }
        
        int m = 1;
        
        for (int i : H.keySet()) {
            m = Math.max(m, H.get(i).b - H.get(i).a);
        }
        
        return n - m;
    }
}
