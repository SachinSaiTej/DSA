# Remove Duplicates from Sorted List

## Problem
Remove duplicate values from a sorted linked list so that each value appears only once.

## Intuition
Because the list is sorted, duplicate values are adjacent. If the current node and next node have the same value, skip the next node. Otherwise, move forward.

## Java
```java
public ListNode deleteDuplicates(ListNode head) {
    ListNode current = head;

    while (current != null && current.next != null) {
        if (current.val == current.next.val) {
            current.next = current.next.next;
        } else {
            current = current.next;
        }
    }

    return head;
}
```

## Complexity
Time O(n), space O(1).