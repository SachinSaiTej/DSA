# First and Last Position

## Intuition
Run binary search twice: once biased left to find the first occurrence and once biased right to find the last.

## Java
```java
public int[] searchRange(int[]a,int t){return new int[]{bound(a,t,false),bound(a,t,true)};}int bound(int[]a,int t,boolean last){int l=0,r=a.length-1,ans=-1;while(l<=r){int m=l+(r-l)/2;if(a[m]==t){ans=m;if(last)l=m+1;else r=m-1;}else if(a[m]<t)l=m+1;else r=m-1;}return ans;}
```

## Complexity
O(log n) time, O(1) space.