# Reverse Nodes in K-Group

## Problem
Reverse nodes of a linked list in groups of `k`. Leave a final group unchanged if it contains fewer than `k` nodes.

## Intuition
First check whether `k` nodes exist. If they do, reverse exactly those `k` nodes and recursively process the remaining list.

## Java
```java
public ListNode reverseKGroup(ListNode head, int k) {
    ListNode current = head;

    // Check whether a complete group of k nodes exists.
    for (int i = 0; i < k; i++) {
        if (current == null) {
            return head;
        }
        current = current.next;
    }

    // Reverse the current group.
    ListNode previous = null;
    ListNode node = head;

    for (int i = 0; i < k; i++) {
        ListNode next = node.next;
        node.next = previous;
        previous = node;
        node = next;
    }

    // Connect the current group to the reversed remainder.
    head.next = reverseKGroup(node, k);

    return previous;
}
```

## Complexity
Time O(n), space O(n/k) for the recursion stack.