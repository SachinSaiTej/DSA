# Bitwise AND of Numbers Range

## Problem
Find the bitwise AND of every number in the inclusive range `[left, right]`.

## Intuition
Any bit that changes within the range will eventually contain both 0 and 1, so it disappears from the AND. Keep removing the lowest set bit from `right` until `right <= left`.

## Java
```java
public int rangeBitwiseAnd(int left,int right){while(right>left)right&=right-1;return right;}
```

## Complexity
Time O(32), space O(1).