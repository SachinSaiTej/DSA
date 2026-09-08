# Binary Search

## Intuition
On a sorted array, compare the middle value with the target and discard half the search space each step.

## Java
```java
public int search(int[]a,int t){int l=0,r=a.length-1;while(l<=r){int m=l+(r-l)/2;if(a[m]==t)return m;if(a[m]<t)l=m+1;else r=m-1;}return -1;}
```

## Complexity
O(log n) time, O(1) space.