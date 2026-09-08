# Kth Largest Element in an Array

## Problem
Return the kth largest element without fully sorting the array.

## Intuition
Maintain a min-heap of size `k`. The heap contains the current k largest values; its root is the kth largest.

## Java
```java
public int findKthLargest(int[] nums, int k) {
    PriorityQueue<Integer> pq = new PriorityQueue<>();
    for (int x : nums) {
        pq.offer(x);
        if (pq.size() > k) pq.poll();
    }
    return pq.peek();
}
```

## Complexity
Time O(n log k), space O(k).