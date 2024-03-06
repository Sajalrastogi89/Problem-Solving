# Intuition
The problem involves determining whether a linked list has a cycle. We can use the "two-pointer" or "fast-slow" approach, where one pointer moves at twice the speed of the other. If there's a cycle, the fast pointer will eventually catch up to the slow pointer.

# Approach
We initialize two pointers, slow and fast, both starting from the head of the linked list. The slow pointer moves one step at a time, while the fast pointer moves two steps at a time. If there's a cycle, the two pointers will meet at some point. We iterate until either the pointers meet or one of them reaches the end of the list.

# Complexity
- Time complexity:
  - In the worst case, both pointers traverse the linked list once. Thus, the time complexity is O(n), where n is the number of nodes in the linked list.
- Space complexity:
  - We only use two pointers, slow and fast, regardless of the size of the linked list. Thus, the space complexity is O(1).

# Code
```java
// class ListNode {
//     int val;
//     ListNode next;
//     ListNode(int x) {
//         val = x;
//         next = null;
//     }
// }

public class Solution {
    public boolean hasCycle(ListNode head) {
        if (head == null)
            return false;
            
        ListNode slow = head;
        ListNode fast = head.next;
        
        while (slow != fast) {
            if (slow == null || fast == null || fast.next == null)
                return false;
            
            slow = slow.next;
            fast = fast.next.next;
        }
        
        return true;
    }
}
