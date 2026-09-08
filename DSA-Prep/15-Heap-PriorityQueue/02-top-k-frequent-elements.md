# Top K Frequent Elements

## Problem
Return the `k` most frequent elements.

## Intuition
Count frequencies, then keep a min-heap ordered by frequency. If the heap grows beyond k, remove the least frequent element.

## Java
```java
public int[] topKFrequent(int[] nums, int k) {
    Map<Integer,Integer> freq = new HashMap<>();
    for (int x : nums) freq.merge(x, 1, Integer::sum);
    PriorityQueue<Integer> pq = new PriorityQueue<>((a,b) -> freq.get(a) - freq.get(b));
    for (int x : freq.keySet()) {
        pq.offer(x);
        if (pq.size() > k) pq.poll();
    }
    int[] ans = new int[k];
    for (int i = k - 1; i >= 0; i--) ans[i] = pq.poll();
    return ans;
}
```

## Complexity
Time O(n log k), space O(n).