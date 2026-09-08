# Rotate Array

## Problem
Rotate an array to the right by `k` positions.

## Intuition
Use the reversal technique: reverse the whole array, reverse the first `k` elements, then reverse the remaining elements.

## Java
```java
public void rotate(int[] nums, int k) {
    k %= nums.length;
    reverse(nums, 0, nums.length - 1);
    reverse(nums, 0, k - 1);
    reverse(nums, k, nums.length - 1);
}

private void reverse(int[] nums, int l, int r) {
    while (l < r) {
        int temp = nums[l];
        nums[l++] = nums[r];
        nums[r--] = temp;
    }
}
```

## Complexity
Time O(n), space O(1).

## Example
`[1,2,3,4,5,6,7]`, `k=3` → `[5,6,7,1,2,3,4]`.