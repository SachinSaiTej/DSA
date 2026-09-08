# Sum of Two Integers

## Problem
Add two integers without using `+` or `-`.

## Intuition
XOR gives addition without carries; AND followed by a left shift gives the carry. Repeat until no carry remains.

## Java
```java
public int getSum(int a,int b){while(b!=0){int carry=(a&b)<<1;a^=b;b=carry;}return a;}
```

## Complexity
Time O(32), space O(1).