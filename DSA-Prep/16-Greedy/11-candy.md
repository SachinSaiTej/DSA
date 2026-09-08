# Candy

## Problem
Give each child at least one candy, and children with a higher rating than an adjacent child must receive more candies. Minimize the total.

## Intuition
One left-to-right pass handles increasing runs; one right-to-left pass handles decreasing runs. For each child take the larger requirement from both directions.

## Java
```java
public int candy(int[]r){int n=r.length;if(n==0)return 0;int[]c=new int[n];Arrays.fill(c,1);for(int i=1;i<n;i++)if(r[i]>r[i-1])c[i]=c[i-1]+1;for(int i=n-2;i>=0;i--)if(r[i]>r[i+1])c[i]=Math.max(c[i],c[i+1]+1);int s=0;for(int x:c)s+=x;return s;}
```

## Complexity
O(n) time and O(n) space.