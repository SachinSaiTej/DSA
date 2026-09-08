# Merge Two Sorted Lists

## Problem
Merge two sorted singly linked lists into one sorted list.

## Intuition
Compare the current nodes of both lists. Attach the smaller node and advance that list. A dummy node makes the pointer manipulation simple.

## Java
```java
public ListNode mergeTwoLists(ListNode a, ListNode b) {
    ListNode dummy = new ListNode(0);
    ListNode curr = dummy;
    while (a != null && b != null) {
        if (a.val <= b.val) { curr.next = a; a = a.next; }
        else { curr.next = b; b = b.next; }
        curr = curr.next;
    }
    curr.next = (a != null) ? a : b;
    return dummy.next;
}
```

## Complexity
Time O(n + m), space O(1) extra.

## Interview Point
The dummy node avoids special handling for the first element.