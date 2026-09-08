# Square Root of X

## Intuition
Binary-search the largest integer whose square is at most x. Use division instead of multiplication to avoid overflow.

## Java
```java
public int mySqrt(int x){int l=0,r=x<2?x:x/2,ans=0;while(l<=r){int m=l+(r-l)/2;if(m<=x/m){ans=m;l=m+1;}else r=m-1;}return ans;}
```

## Complexity
O(log x) time, O(1) space.