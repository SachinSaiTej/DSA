# Power of Two

## Problem
Determine whether an integer is a power of two.

## Intuition
A positive power of two has exactly one set bit, so `n & (n-1)` is zero.

## Java
```java
public boolean isPowerOfTwo(int n){return n>0&&(n&(n-1))==0;}
```

## Complexity
Time O(1), space O(1).