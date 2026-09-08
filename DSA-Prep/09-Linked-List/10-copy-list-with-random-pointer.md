# Copy List with Random Pointer

## Problem
Deep-copy a linked list where every node has `next` and `random` pointers.

## Intuition
Interleave copied nodes after their originals. Then `original.random.next` points to the copied random node. Finally, separate the original and copied lists.

## Java
```java
public Node copyRandomList(Node head) {
    if (head == null) {
        return null;
    }

    // Step 1: Insert each copy immediately after its original node.
    for (Node current = head; current != null; current = current.next.next) {
        Node copy = new Node(current.val);
        copy.next = current.next;
        current.next = copy;
    }

    // Step 2: Set the random pointers of the copied nodes.
    for (Node current = head; current != null; current = current.next.next) {
        if (current.random != null) {
            current.next.random = current.random.next;
        }
    }

    // Step 3: Separate the copied list from the original list.
    Node dummy = new Node(0);
    Node tail = dummy;

    for (Node current = head; current != null;) {
        Node copy = current.next;
        current.next = copy.next;

        tail.next = copy;
        tail = copy;

        current = current.next;
    }

    return dummy.next;
}
```

## Complexity
Time O(n), extra space O(1) excluding the copied nodes.