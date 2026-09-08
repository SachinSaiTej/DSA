# Longest Increasing Subsequence

## Problem
Find the length of the longest strictly increasing subsequence.

## Intuition
Maintain `dp[i]` as the best subsequence ending at `i`. For O(n log n), maintain the smallest possible tail for every subsequence length.

## Java
```java
public int lengthOfLIS(int[]a){int[]tail=new int[a.length];int size=0;for(int x:a){int l=0,r=size;while(l<r){int m=(l+r)/2;if(tail[m]<x)l=m+1;else r=m;}tail[l]=x;if(l==size)size++;}return size;}
```

## Complexity
Time O(n log n), space O(n).