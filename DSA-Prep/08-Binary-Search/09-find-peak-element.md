# Find Peak Element

## Intuition
If `a[mid] < a[mid+1]`, a peak exists to the right; otherwise a peak exists at mid or left.

## Java
```java
public int findPeakElement(int[]a){int l=0,r=a.length-1;while(l<r){int m=l+(r-l)/2;if(a[m]<a[m+1])l=m+1;else r=m;}return l;}
```

## Complexity
O(log n) time, O(1) space.