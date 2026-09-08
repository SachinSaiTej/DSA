# Subarray Sum Equals K

## Intuition
For current prefix sum `sum`, a previous prefix `sum-k` means the subarray between them sums to k. Store prefix frequencies.

## Java
```java
public int subarraySum(int[] a,int k){Map<Integer,Integer> m=new HashMap<>();m.put(0,1);int sum=0,ans=0;for(int x:a){sum+=x;ans+=m.getOrDefault(sum-k,0);m.merge(sum,1,Integer::sum);}return ans;}
```

## Complexity
O(n) time, O(n) space.