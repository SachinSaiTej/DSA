# Merge K Sorted Lists

## Intuition
Put the head of every list in a min-heap. Repeatedly take the smallest node and add its next node.

## Java
```java
public ListNode mergeKLists(ListNode[] lists){PriorityQueue<ListNode>pq=new PriorityQueue<>((a,b)->Integer.compare(a.val,b.val));for(ListNode n:lists)if(n!=null)pq.offer(n);ListNode d=new ListNode(0),t=d;while(!pq.isEmpty()){ListNode n=pq.poll();t.next=n;t=n;if(n.next!=null)pq.offer(n.next);}return d.next;}
```

## Complexity
O(N log k) time and O(k) heap space, where N is total nodes.