# Search in Rotated Sorted Array

## Intuition
At least one half is sorted. Determine which half is sorted, then check whether the target lies inside it.

## Java
```java
public int search(int[]a,int t){int l=0,r=a.length-1;while(l<=r){int m=l+(r-l)/2;if(a[m]==t)return m;if(a[l]<=a[m]){if(a[l]<=t&&t<a[m])r=m-1;else l=m+1;}else{if(a[m]<t&&t<=a[r])l=m+1;else r=m-1;}}return -1;}
```

## Complexity
O(log n) time, O(1) space.