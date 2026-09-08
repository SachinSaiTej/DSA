# Palindrome Linked List

## Problem
Determine whether a singly linked list reads the same forward and backward.

## Intuition
Find the middle, reverse the second half, then compare both halves node by node.

## Java
```java
public boolean isPalindrome(ListNode head) {
    if (head == null || head.next == null) return true;
    ListNode slow = head, fast = head;
    while (fast != null && fast.next != null) {
        slow = slow.next; fast = fast.next.next;
    }
    ListNode second = reverseList(slow);
    ListNode first = head;
    while (second != null) {
        if (first.val != second.val) return false;
        first = first.next; second = second.next;
    }
    return true;
}

private ListNode reverseList(ListNode head) {
    ListNode prev = null;
    while (head != null) {
        ListNode next = head.next;
        head.next = prev; prev = head; head = next;
    }
    return prev;
}
```

## Complexity
Time O(n), space O(1).