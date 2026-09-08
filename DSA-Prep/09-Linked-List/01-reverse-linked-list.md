# Reverse Linked List

## Intuition
Walk through the list while reversing each `next` pointer. Keep `prev` as the already-reversed portion.

## Java
```java
public ListNode reverseList(ListNode head){ListNode prev=null;while(head!=null){ListNode next=head.next;head.next=prev;prev=head;head=next;}return prev;}
```

## Complexity
O(n) time, O(1) space.