# Minimum Cost to Fill Weight

## Intuition
The problem requires finding the minimum cost to fill a knapsack of weight `W` using items that have specific costs. This can be approached using dynamic programming to keep track of the minimum cost for each weight up to `W`.

## Approach
1. **Initialize DP Array**:
   - Create a 2D DP array `dp` where `dp[i][j]` represents the minimum cost to achieve weight `j` using the first `i` items.
   - Initialize the DP array with `-1` to indicate that the value hasn't been computed yet.

2. **Recursive Helper Function**:
   - Define a helper function `helper(ind, W, cost, dp)` that returns the minimum cost to achieve weight `W` using items up to index `ind`.
   - Base Cases:
     - If `W` is `0`, return `0` since no cost is needed to achieve zero weight.
     - If `ind` is less than `0`, return a large value (infinity) to indicate that it's impossible to achieve the weight with no items.
   - Memoization:
     - If the value is already computed (`dp[ind][W] != -1`), return the stored value.

3. **Choice Diagram**:
   - **Not Take**: Skip the current item and consider the previous items with the same weight.
   - **Take**: If the current item is available (`cost[ind] != -1`) and can be included (`W >= ind + 1`), include the item and add its cost to the result of the remaining weight.

4. **Final Result**:
   - Start the recursion from the last item and the target weight.
   - Return the result. If the result is equal to the large value, return `-1` indicating that it's not possible to achieve the weight.

## Complexity
- **Time complexity**:
  - The approach uses memoization to avoid redundant calculations, resulting in a time complexity of $$O(N \times W)$$ where `N` is the number of items and `W` is the target weight.

- **Space complexity**:
  - The space complexity is $$O(N \times W)$$ due to the DP array used for memoization.

## Code
```java
class Solution {
    public int minimumCost(int N, int W, int[] cost) {
        int[][] dp = new int[N + 1][W + 1];
        for (int[] row : dp)
            Arrays.fill(row, -1);
        int res = helper(N - 1, W, cost, dp);    
        return res == 100000009 ? -1 : res;
    }
    
    public static int helper(int ind, int W, int[] cost, int[][] dp) {
        if (W == 0) {
            return 0;
        }
        if (ind < 0) {
            return 100000009; // A large number to represent infinity
        }
        if (dp[ind][W] != -1) {
            return dp[ind][W];
        }
        int notTake = helper(ind - 1, W, cost, dp);
        int take = Integer.MAX_VALUE;
        if (cost[ind] != -1 && W >= ind + 1) {
            take = cost[ind] + helper(ind, W - (ind + 1), cost, dp);
        }
        return dp[ind][W] = Math.min(take, notTake);
    }
}
