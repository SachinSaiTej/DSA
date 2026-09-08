# Rotate List

## Problem
Rotate a linked list to the right by `k` positions.

## Intuition
Connect the tail to the head to form a circular list. Then break the circle at the correct position. Reduce `k` using `k % n`.

## Java
```java
public ListNode rotateRight(ListNode head, int k) {
    if (head == null || head.next == null) {
        return head;
    }

    int length = 1;
    ListNode tail = head;

    while (tail.next != null) {
        tail = tail.next;
        length++;
    }

    k %= length;

    if (k == 0) {
        return head;
    }

    tail.next = head;

    for (int i = 0; i < length - k; i++) {
        tail = tail.next;
    }

    ListNode newHead = tail.next;
    tail.next = null;

    return newHead;
}
```

## Complexity
Time O(n), space O(1).