# Continuous Subarray Sum

## Intuition
If two prefix sums have the same remainder modulo k, their difference is divisible by k. Store the earliest index for each remainder.

## Java
```java
public boolean checkSubarraySum(int[] a,int k){Map<Integer,Integer> m=new HashMap<>();m.put(0,-1);int sum=0;for(int i=0;i<a.length;i++){sum=(sum+a[i])%k;if(sum<0)sum+=k;if(m.containsKey(sum)){if(i-m.get(sum)>1)return true;}else m.put(sum,i);}return false;}
```

## Complexity
O(n) time, O(k) space.