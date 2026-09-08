# Kth Largest Element

## Problem
Return the kth largest element in an unsorted array.

## Intuition
Keep a min-heap of size `k`. It stores the k largest values seen so far, and its root is the kth largest.

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