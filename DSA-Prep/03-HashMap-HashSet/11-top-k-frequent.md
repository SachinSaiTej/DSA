# Top K Frequent Elements

## Problem
Return the `k` elements that occur most frequently.

## Intuition
Count frequencies, then maintain a min-heap of size k ordered by frequency. The least frequent candidate is removed when the heap grows too large.

## Java
```java
public int[] topKFrequent(int[] nums, int k) {
    Map<Integer,Integer> freq=new HashMap<>();
    for(int x:nums) freq.merge(x,1,Integer::sum);
    PriorityQueue<Integer> pq=new PriorityQueue<>((a,b)->Integer.compare(freq.get(a),freq.get(b)));
    for(int x:freq.keySet()){
        pq.offer(x);
        if(pq.size()>k) pq.poll();
    }
    int[] ans=new int[k];
    for(int i=k-1;i>=0;i--) ans[i]=pq.poll();
    return ans;
}
```

## Complexity
Time O(n log k), space O(n).