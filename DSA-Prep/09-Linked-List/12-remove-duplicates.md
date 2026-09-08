# Remove Duplicates from Sorted List

## Intuition
Because the list is sorted, duplicates are adjacent. If the next node has the same value, skip it; otherwise advance.

## Java
```java
public ListNode deleteDuplicates(ListNode head){ListNode c=head;while(c!=null&&c.next!=null){if(c.val==c.next.val)c.next=c.next.next;else c=c.next;}return head;}
```

## Complexity
O(n) time, O(1) space.