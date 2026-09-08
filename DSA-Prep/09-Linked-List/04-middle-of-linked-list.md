# Middle of Linked List

## Problem
Return the middle node of a singly linked list. For an even length, return the second middle node.

## Intuition
Use slow and fast pointers. Slow moves one step while fast moves two, so slow reaches the middle when fast reaches the end.

## Java
```java
public ListNode middleNode(ListNode head) {
    ListNode slow = head, fast = head;
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
    }
    return slow;
}
```

## Complexity
Time O(n), space O(1).