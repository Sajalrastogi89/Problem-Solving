# Problem: Minimum Remove to Make Valid Parentheses

## Intuition
The problem seems to involve processing a string to make it valid in terms of parentheses. Invalid parentheses are those that do not have a matching opening or closing parenthesis. The intuition might involve using a stack to keep track of opening parentheses, and whenever a closing parenthesis is encountered, ensuring it has a matching opening parenthesis.

## Approach
1. **Stack Approach**: 
   - Initialize an empty stack to keep track of opening parentheses and their indices.
   - Iterate through the string:
     - If the current character is an opening parenthesis '(', push its index onto the stack.
     - If it's a closing parenthesis ')':
       - If the stack is empty or the top of the stack contains a closing parenthesis, push its index onto the stack.
       - Otherwise, pop the top index from the stack, indicating a valid pair.
   - After iterating through the string, remove any remaining unpaired parentheses from the string using their stored indices.
   - Return the modified string.

## Complexity
- Time complexity: 
  - The time complexity of iterating through the string is O(n).
  - Deleting characters from a StringBuilder also takes O(n) time in the worst case.
  - So, the overall time complexity is O(n).

- Space complexity:
  - The space complexity is O(n) due to the stack and the StringBuilder.

## Code
```java
class Solution {
    public String minRemoveToMakeValid(String s) {
        Stack<Pair<Character,Integer>> parenthesesStack = new Stack<>();
        for(int i = 0; i < s.length(); i++) {
            if(s.charAt(i) == '(')
                parenthesesStack.push(new Pair<>('(', i));
            else if(s.charAt(i) == ')') {
                if(parenthesesStack.isEmpty() || parenthesesStack.peek().getKey() == ')') {
                    parenthesesStack.push(new Pair<>(')', i));
                } else {
                    parenthesesStack.pop();
                }
            }
        }
        
        StringBuilder modifiedString = new StringBuilder(s);
        while(!parenthesesStack.isEmpty()) {
            int indexToRemove = parenthesesStack.pop().getValue();
            modifiedString.deleteCharAt(indexToRemove);
        }
        
        return modifiedString.toString();
    }
}
