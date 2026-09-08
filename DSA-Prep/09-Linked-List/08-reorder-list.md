# Reorder List

## Problem
Reorder `L0 → L1 → ... → Ln` into `L0 → Ln → L1 → Ln-1 ...`.

## Intuition
Split at the middle, reverse the second half, then merge the two halves alternately.

## Java
```java
public void reorderList(ListNode head) {
    if (head == null || head.next == null) return;
    ListNode slow = head, fast = head;
    while (fast.next != null && fast.next.next != null) {
        slow = slow.next; fast = fast.next.next;
    }
    ListNode second = reverseList(slow.next);
    slow.next = null;
    ListNode first = head;
    while (second != null) {
        ListNode a = first.next, b = second.next;
        first.next = second;
        second.next = a;
        first = a;
        second = b;
    }
}

private ListNode reverseList(ListNode head) {
    ListNode prev = null;
    while (head != null) {
        ListNode next = head.next;
        head.next = prev;
        prev = head;
        head = next;
    }
    return prev;
}
```

## Complexity
Time O(n), space O(1).