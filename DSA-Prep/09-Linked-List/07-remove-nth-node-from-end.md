# Remove Nth Node From End

## Problem
Remove the nth node from the end of a singly linked list.

## Intuition
Use a dummy node and keep `fast` exactly `n` nodes ahead of `slow`. Move both until `fast` reaches the end; `slow.next` is the node to remove.

## Java
```java
public ListNode removeNthFromEnd(ListNode head, int n) {
    ListNode dummy = new ListNode(0);
    dummy.next = head;
    ListNode fast = dummy, slow = dummy;
    for (int i = 0; i < n; i++) fast = fast.next;
    while (fast.next != null) {
        fast = fast.next;
        slow = slow.next;
    }
    slow.next = slow.next.next;
    return dummy.next;
}
```

## Complexity
Time O(n), space O(1).