# First Negative in Every Window

## Problem
For every window of size `k`, return its first negative element, or `0` if none exists.

## Intuition
Maintain a deque of indices of negative values. Remove indices outside the window; the front is the first negative.

## Java
```java
public long[] firstNegative(int[] a,int k){
 int n=a.length;long[] ans=new long[n-k+1];Deque<Integer> q=new ArrayDeque<>();
 for(int i=0;i<n;i++){if(a[i]<0)q.addLast(i);if(!q.isEmpty()&&q.peekFirst()<=i-k)q.pollFirst();if(i>=k-1)ans[i-k+1]=q.isEmpty()?0:a[q.peekFirst()];}return ans;
}
```

## Complexity
O(n) time and O(k) space.