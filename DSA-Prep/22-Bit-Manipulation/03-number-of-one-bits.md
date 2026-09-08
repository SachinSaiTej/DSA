# Number of 1 Bits

## Problem
Return the number of set bits in an integer.

## Intuition
`n & (n - 1)` removes the lowest set bit. Repeat until zero.

## Java
```java
public int hammingWeight(int n){int count=0;while(n!=0){n&=n-1;count++;}return count;}
```

## Complexity
Time O(number of set bits), space O(1).