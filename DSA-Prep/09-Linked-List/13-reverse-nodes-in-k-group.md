# Reverse Nodes in K-Group

## Problem
Reverse nodes of a linked list in groups of `k`. Leave a final group unchanged if it has fewer than `k` nodes.

## Intuition
Check whether `k` nodes exist, reverse exactly that block, then recursively/process the remainder.

## Java
```java
public ListNode reverseKGroup(ListNode head, int k) {
    ListNode cur = head;
    for (int i = 0; i < k; i++) {
        if (cur == null) return head;
        cur = cur.next;
    }
    ListNode prev = null, node = head;
    for (int i = 0; i < k; i++) {
        ListNode next = node.next;
        node.next = prev;
        prev = node;
        node = next;
    }
    head.next = reverseKGroup(node, k);
    return prev;
}
```

## Complexity
Time O(n), space O(n/k) recursion stack.