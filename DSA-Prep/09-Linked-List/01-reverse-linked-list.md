# Reverse Linked List

## Problem
Reverse a singly linked list and return its new head.

## Intuition
Keep three pointers: `prev`, `curr`, and `next`. Reverse `curr.next` one node at a time.

## Java
```java
public ListNode reverseList(ListNode head) {
    ListNode prev = null;
    ListNode curr = head;

    while (curr != null) {
        ListNode next = curr.next;
        curr.next = prev;
        prev = curr;
        curr = next;
    }

    return prev;
}
```

## Complexity
Time O(n), space O(1).

## Interview Point
Never change `curr.next` before saving the original next node.