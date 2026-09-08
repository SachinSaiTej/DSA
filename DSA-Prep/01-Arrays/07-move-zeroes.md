# Move Zeroes

## Problem
Move all zeroes to the end of the array while preserving the relative order of non-zero elements.

## Intuition
Keep a `write` pointer for the next position where a non-zero value belongs. Scan once and swap each non-zero into that position.

## Java
```java
public void moveZeroes(int[] nums) {
    int write = 0;
    for (int read = 0; read < nums.length; read++) {
        if (nums[read] != 0) {
            int temp = nums[write];
            nums[write] = nums[read];
            nums[read] = temp;
            write++;
        }
    }
}
```

## Complexity
Time O(n), space O(1).