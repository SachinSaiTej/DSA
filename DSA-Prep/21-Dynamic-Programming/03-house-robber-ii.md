# House Robber II

## Problem
Houses form a circle, so the first and last houses are adjacent. Maximize robbed money without robbing adjacent houses.

## Intuition
Because first and last cannot both be chosen, solve two linear cases: exclude the first or exclude the last.

## Java
```java
public int rob(int[]a){if(a.length==1)return a[0];return Math.max(linear(a,0,a.length-2),linear(a,1,a.length-1));}
int linear(int[]a,int l,int r){int p2=0,p1=0;for(int i=l;i<=r;i++){int c=Math.max(p1,p2+a[i]);p2=p1;p1=c;}return p1;}
```

## Complexity
Time O(n), space O(1).