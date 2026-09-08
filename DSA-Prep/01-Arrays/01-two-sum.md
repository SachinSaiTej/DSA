# Two Sum

## Problem
Given an integer array `nums` and a target, return the indices of two numbers whose sum equals the target.

## Intuition
For every number `x`, we need `target - x`. Store numbers we have already seen in a `HashMap` so the complement can be found in O(1) average time.

## Approach
1. Traverse the array once.
2. Calculate `complement = target - nums[i]`.
3. If the complement is already in the map, return its index and `i`.
4. Otherwise store `nums[i] -> i`.

## Java
```java
public int[] twoSum(int[] nums, int target) {
    Map<Integer, Integer> map = new HashMap<>();

    for (int i = 0; i < nums.length; i++) {
        int complement = target - nums[i];
        if (map.containsKey(complement)) {
            return new int[]{map.get(complement), i};
        }
        map.put(nums[i], i);
    }

    return new int[0];
}
```

## Complexity
- Time: O(n) average
- Space: O(n)

## Interview Point
The key optimization is trading O(n) extra space for a one-pass O(n) solution instead of the O(n²) brute-force approach.