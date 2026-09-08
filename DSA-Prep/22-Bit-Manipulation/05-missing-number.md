# Missing Number

## Problem
An array contains distinct values from `0..n` with one missing. Find it.

## Intuition
XOR every index and value. Equal values cancel, leaving the missing number.

## Java
```java
public int missingNumber(int[]a){int x=a.length;for(int i=0;i<a.length;i++)x^=i^a[i];return x;}
```

## Complexity
Time O(n), space O(1).