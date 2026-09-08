# Partition List

## Intuition
Build two lists: nodes smaller than x and nodes at least x. Join them at the end while preserving relative order.

## Java
```java
public ListNode partition(ListNode h,int x){ListNode a=new ListNode(0),b=new ListNode(0),p=a,q=b;while(h!=null){if(h.val<x){p.next=h;p=p.next;}else{q.next=h;q=q.next;}h=h.next;}q.next=null;p.next=b.next;return a.next;}
```

## Complexity
O(n) time, O(1) extra space.