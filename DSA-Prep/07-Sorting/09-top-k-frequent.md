# Top K Frequent Elements

## Intuition
Count frequencies and keep the k most frequent values in a min-heap ordered by frequency.

## Java
```java
public int[] topKFrequent(int[]a,int k){Map<Integer,Integer>f=new HashMap<>();for(int x:a)f.merge(x,1,Integer::sum);PriorityQueue<Integer>q=new PriorityQueue<>((x,y)->f.get(x)-f.get(y));for(int x:f.keySet()){q.offer(x);if(q.size()>k)q.poll();}int[]o=new int[k];for(int i=k-1;i>=0;i--)o[i]=q.poll();return o;}
```

## Complexity
O(n log k) time, O(n) space.