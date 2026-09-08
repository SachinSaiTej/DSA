# Add Two Numbers

## Problem
Two linked lists represent non-negative integers in reverse digit order. Return their sum in the same format.

## Intuition
Add corresponding digits with a carry, exactly like elementary addition.

## Java
```java
public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
    ListNode dummy = new ListNode(0), curr = dummy;
    int carry = 0;
    while (l1 != null || l2 != null || carry != 0) {
        int sum = carry;
        if (l1 != null) { sum += l1.val; l1 = l1.next; }
        if (l2 != null) { sum += l2.val; l2 = l2.next; }
        curr.next = new ListNode(sum % 10);
        carry = sum / 10;
        curr = curr.next;
    }
    return dummy.next;
}
```

## Complexity
Time O(max(n,m)), space O(max(n,m)) for the output.