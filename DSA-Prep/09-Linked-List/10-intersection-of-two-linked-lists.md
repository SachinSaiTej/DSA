# Intersection of Two Linked Lists

## Problem
Find the first node shared by two singly linked lists, or return `null`.

## Intuition
Let pointer A traverse list A then list B, and pointer B traverse list B then list A. Both travel the same total distance, so they align at the intersection.

## Java
```java
public ListNode getIntersectionNode(ListNode a, ListNode b) {
    ListNode p = a, q = b;
    while (p != q) {
        p = (p == null) ? b : p.next;
        q = (q == null) ? a : q.next;
    }
    return p;
}
```

## Complexity
Time O(n + m), space O(1).