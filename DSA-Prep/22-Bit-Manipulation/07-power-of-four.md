# Power of Four

## Problem
Determine whether an integer is a power of four.

## Intuition
It must first be a power of two. Additionally, its single set bit must be in an odd bit position; the mask `0x55555555` identifies those positions.

## Java
```java
public boolean isPowerOfFour(int n){return n>0&&(n&(n-1))==0&&(n&0x55555555)!=0;}
```

## Complexity
Time O(1), space O(1).