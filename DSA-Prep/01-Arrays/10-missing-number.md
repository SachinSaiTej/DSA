# Missing Number

## Problem
An array contains distinct numbers from `0` to `n` with exactly one missing. Find the missing number.

## Intuition
XOR all indices and all values. Every present value appears twice and cancels, leaving only the missing value.

## Java
```java
public int missingNumber(int[] nums) {
    int result = nums.length;
    for (int i = 0; i < nums.length; i++) {
        result ^= i;
        result ^= nums[i];
    }
    return result;
}
```

## Complexity
Time O(n), space O(1).