# Two Sum

## Problem
Find two indices whose values add up to the target.

## Intuition
For each value `x`, we need `target - x`. Store previously seen values in a map from value to index, so the complement can be found in O(1) average time.

## Java
```java
public int[] twoSum(int[] nums, int target) {
    Map<Integer, Integer> seen = new HashMap<>();
    for (int i = 0; i < nums.length; i++) {
        int need = target - nums[i];
        if (seen.containsKey(need)) return new int[]{seen.get(need), i};
        seen.put(nums[i], i);
    }
    return new int[0];
}
```

## Complexity
Time O(n) average, space O(n).