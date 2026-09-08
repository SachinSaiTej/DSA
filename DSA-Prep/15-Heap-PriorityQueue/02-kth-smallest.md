# Kth Smallest Element

## Intuition
Maintain a max-heap of size `k`. It stores the k smallest values seen; the largest among them is the kth smallest.

## Java
```java
public int kthSmallest(int[]a,int k){PriorityQueue<Integer>pq=new PriorityQueue<>(Collections.reverseOrder());for(int x:a){pq.offer(x);if(pq.size()>k)pq.poll();}return pq.peek();}
```

## Complexity
O(n log k) time and O(k) space.