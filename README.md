# Remove nth node from end of the linked list
## https://leetcode.com/problems/remove-nth-node-from-end-of-list

Given a linked list, remove the n-th node from the end of list and return its head.

Example:

Given linked list: 1->2->3->4->5, and n = 2.

After removing the second node from the end, the linked list becomes 1->2->3->5.

**Note:**

Given n will always be valid.

**Follow up:**

Could you do this in one pass?

## Implementation :

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        if(head == null)
            return head;
        int length = 0;
        ListNode headReference = head;
        while(headReference != null){
            length++;
            headReference = headReference.next;
        }
        if(length == n){
            head = head.next;
            return head;
        }
        ListNode temp = head;
        for(int i = 1; i < length - n; i++){
            temp = temp.next;
        }
        ListNode toBeDeleted = temp.next;
        temp.next = toBeDeleted.next;
        
        return head;
    }
}
```
