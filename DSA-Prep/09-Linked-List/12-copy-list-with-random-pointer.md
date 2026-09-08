# Copy List with Random Pointer

## Problem
Deep-copy a linked list where every node has `next` and `random` pointers.

## Intuition
Interleave copied nodes after their originals. Then random pointers can be assigned using `original.random.next`. Finally separate the two lists.

## Java
```java
public Node copyRandomList(Node head) {
    if (head == null) return null;
    for (Node cur = head; cur != null; cur = cur.next.next) {
        Node copy = new Node(cur.val);
        copy.next = cur.next;
        cur.next = copy;
    }
    for (Node cur = head; cur != null; cur = cur.next.next) {
        if (cur.random != null) cur.next.random = cur.random.next;
    }
    Node dummy = new Node(0), tail = dummy;
    for (Node cur = head; cur != null;) {
        Node copy = cur.next;
        cur.next = copy.next;
        tail.next = copy;
        tail = copy;
        cur = cur.next;
    }
    return dummy.next;
}
```

## Complexity
Time O(n), extra space O(1) excluding the copied nodes.