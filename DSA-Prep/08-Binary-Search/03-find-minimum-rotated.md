# Find Minimum in Rotated Sorted Array

## Intuition
Compare middle with the right boundary. If middle is greater, the minimum is to the right; otherwise it is at mid or left.

## Java
```java
public int findMin(int[]a){int l=0,r=a.length-1;while(l<r){int m=l+(r-l)/2;if(a[m]>a[r])l=m+1;else r=m;}return a[l];}
```

## Complexity
O(log n) time, O(1) space.