# 21. Merge Two Sorted Lists

- Date: 02/18/2021 
- Language: Java
- [Question Link](https://leetcode.com/problems/merge-two-sorted-lists/)

### Approach 1
Create dummy `Linked List`. Since two list is alreayd sorted, we can comapre heads of the two lists
and link them in the correct order to dummy at the same time.

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        ListNode dummy = new ListNode(0);
        ListNode head = dummy;
        
        while(l1!=null && l2!=null){
            if(l1.val <= l2.val){
                dummy.next = l1;
                l1 = l1.next;
            } else {
                dummy.next = l2;
                l2 = l2.next;
            }
            dummy = dummy.next;
        }
        
        if(l1 != null){
            dummy.next = l1;
        } else if (l2 != null){
            dummy.next = l2;
        }
        
        return head.next;
    }
}
```

- Runtime: 0 ms (>100%)
- Memory Usage: 38.6 MB (<38.24%)
