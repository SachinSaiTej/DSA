# Search Insert Position

## Intuition
Standard binary search. If target is absent, `l` ends exactly at the first position where target can be inserted.

## Java
```java
public int searchInsert(int[]a,int t){int l=0,r=a.length;while(l<r){int m=l+(r-l)/2;if(a[m]<t)l=m+1;else r=m;}return l;}
```

## Complexity
O(log n) time, O(1) space.