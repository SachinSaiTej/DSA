# Counting Bits

## Problem
For every number from 0 to `n`, return its number of set bits.

## Intuition
`i >> 1` removes the last bit, so `bits[i] = bits[i >> 1] + (i & 1)`.

## Java
```java
public int[] countBits(int n) {
    int[] bits=new int[n+1];
    for(int i=1;i<=n;i++) bits[i]=bits[i>>1]+(i&1);
    return bits;
}
```

## Complexity
Time O(n), space O(n).