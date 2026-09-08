# Maximum Subarray

## Problem
Find the contiguous subarray with the largest sum.

## Intuition
At each element, decide whether to extend the current subarray or start a new one. This is Kadane's algorithm.

## Java
```java
public int maxSubArray(int[] nums) {
    int current = nums[0];
    int best = nums[0];

    for (int i = 1; i < nums.length; i++) {
        current = Math.max(nums[i], current + nums[i]);
        best = Math.max(best, current);
    }
    return best;
}
```

## Complexity
Time O(n), space O(1).

## Interview Point
`current` means the best sum of a subarray ending exactly at the current index.