# Intuition
The problem requires finding two elements that are repeated in an array. We can employ bitwise XOR to efficiently solve this problem. The key insight is to recognize that if we XOR all elements of the array with all numbers from 1 to n (where n is the size of the array), the result will be XOR of the two repeated elements.

# Approach
Our approach involves utilizing bitwise XOR to find the two repeated elements efficiently. We first calculate the XOR of all elements in the array and XOR of all numbers from 1 to n. Then, we find the rightmost set bit in the XOR result to partition the elements based on this bit. After partitioning, we XOR the elements in each partition separately to find the repeated elements.

# Complexity
- Time complexity:
  - This approach has a time complexity of O(n), where n is the size of the input array.
- Space complexity:
  - The space complexity is O(1) as we use only a constant amount of extra space.

# Code
```java
//User function template for JAVA

class Solution
{
    //Function to find two repeated elements.
   public int[] twoRepeated(int arr[], int n)
    {
        int xorNum = 0;
        for(int i = 0; i < n+2; i++){
            xorNum ^= arr[i];
        }
        for(int i = 1; i <= n; i++){
            xorNum ^= i;
        }
        
        int j = 0;
        int xorCopy = xorNum;
        while((xorCopy & (1<<j)) != (1<<j)){
            j++;
        }
        
        int setBit = 0;
        int unsetBit = 0;
        for(int i = 0; i < n+2; i++){
            if((arr[i]&(1<<j)) == (1<<j)){
                setBit ^= arr[i];
            }else{
                unsetBit ^= arr[i];
            }
        }
        for(int i = 1; i <= n; i++){
            if((i&(1<<j)) == (1<<j)){
                setBit ^= i;
            }else{
                unsetBit ^= i;
            }
        }
        
        int[] ans = new int[2];
        int setCount = 0;
        int unsetCount = 0;
        for(int i = 0; i < n+2; i++){
            if(arr[i] == setBit){
                setCount++;
                if(setCount == 2){
                    ans[0] = setBit;
                    break;
                }
            }else if(arr[i] == unsetBit){
                unsetCount++;
                if(unsetCount == 2){
                    ans[0] = unsetBit;
                    break;
                }
            }
        }
        
        if(ans[0] == setBit){
            ans[1] = unsetBit;
        }else{
            ans[1] = setBit;
        }
        return ans;
    }
}
