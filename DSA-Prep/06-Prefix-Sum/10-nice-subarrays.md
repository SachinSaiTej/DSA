# Count Number of Nice Subarrays

## Intuition
Count subarrays with exactly k odd numbers as `atMost(k) - atMost(k-1)`. The at-most count is a sliding window, and this works because we only track parity.

## Java
```java
public int numberOfSubarrays(int[] a,int k){return atMost(a,k)-atMost(a,k-1);}int atMost(int[]a,int k){int l=0,ans=0;for(int r=0;r<a.length;r++){if((a[r]&1)==1)k--;while(k<0)if((a[l++]&1)==1)k++;ans+=r-l+1;}return ans;}
```

## Complexity
O(n) time, O(1) space.