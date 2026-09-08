# Linked List Cycle

## Problem
Determine whether a linked list contains a cycle.

## Intuition
Floyd's tortoise-and-hare algorithm uses a slow pointer and a fast pointer. If a cycle exists, they eventually meet.

## Java
```java
public boolean hasCycle(ListNode head) {
    ListNode slow = head, fast = head;
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
        if (slow == fast) return true;
    }
    return false;
}
```

## Complexity
Time O(n), space O(1).