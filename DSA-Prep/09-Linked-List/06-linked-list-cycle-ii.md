# Linked List Cycle II

## Problem
Return the node where a cycle begins, or `null` if there is no cycle.

## Intuition
First use slow/fast pointers to detect a meeting point. Then put one pointer at the head and move both one step at a time; their next meeting point is the cycle entry.

## Java
```java
public ListNode detectCycle(ListNode head) {
    ListNode slow = head, fast = head;
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
        if (slow == fast) {
            ListNode p = head;
            while (p != slow) {
                p = p.next;
                slow = slow.next;
            }
            return p;
        }
    }
    return null;
}
```

## Complexity
Time O(n), space O(1).