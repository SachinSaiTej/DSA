# Single Number

## Problem
Every value appears twice except one. Return the value that appears once.

## Intuition
XOR cancels equal values because `x ^ x = 0` and `x ^ 0 = x`.

## Java
```java
public int singleNumber(int[] nums) {
    int ans=0;
    for(int x:nums) ans ^= x;
    return ans;
}
```

## Complexity
Time O(n), space O(1).