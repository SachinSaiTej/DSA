# Kth Largest Element

## Intuition
A min-heap of size k stores the k largest elements seen. Its root is the kth largest.

## Java
```java
public int findKthLargest(int[]a,int k){PriorityQueue<Integer>q=new PriorityQueue<>();for(int x:a){q.offer(x);if(q.size()>k)q.poll();}return q.peek();}
```

## Complexity
O(n log k) time, O(k) space.