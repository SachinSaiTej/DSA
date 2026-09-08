# Reverse Bits

## Problem
Reverse the 32 bits of an unsigned integer.

## Intuition
Read the lowest bit and append it to the result by shifting the result left.

## Java
```java
public int reverseBits(int n){int r=0;for(int i=0;i<32;i++){r=(r<<1)|(n&1);n>>>=1;}return r;}
```

## Complexity
Time O(32), space O(1).