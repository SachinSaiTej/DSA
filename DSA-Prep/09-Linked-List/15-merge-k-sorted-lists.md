# Merge K Sorted Lists

## Intuition
Put the head of every list into a min-heap. Repeatedly remove the smallest node and add its next node.

## Java
```java
public ListNode mergeKLists(ListNode[] lists){PriorityQueue<ListNode>q=new PriorityQueue<>((a,b)->Integer.compare(a.val,b.val));for(ListNode h:lists)if(h!=null)q.offer(h);ListNode d=new ListNode(0),t=d;while(!q.isEmpty()){ListNode n=q.poll();t.next=n;t=n;if(n.next!=null)q.offer(n.next);}return d.next;}
```

## Complexity
O(N log k) time, O(k) heap space.