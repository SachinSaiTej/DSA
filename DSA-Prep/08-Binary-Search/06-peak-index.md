# Peak Index in a Mountain Array

## Intuition
If `a[mid] < a[mid+1]`, we're on the increasing slope, so move right. Otherwise move left, keeping mid as a candidate.

## Java
```java
public int peakIndexInMountainArray(int[]a){int l=0,r=a.length-1;while(l<r){int m=l+(r-l)/2;if(a[m]<a[m+1])l=m+1;else r=m;}return l;}
```

## Complexity
O(log n) time, O(1) space.