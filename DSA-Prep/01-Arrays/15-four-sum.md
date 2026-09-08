# 4Sum

## Problem
Find all unique quadruplets whose values sum to a given target.

## Intuition
Sort the array, fix the first two elements, then use two pointers for the remaining two. This reduces the inner problem to two sum on a sorted array.

## Java
```java
public List<List<Integer>> fourSum(int[] nums, int target) {
    Arrays.sort(nums);
    List<List<Integer>> ans = new ArrayList<>();
    int n = nums.length;

    for (int i = 0; i < n - 3; i++) {
        if (i > 0 && nums[i] == nums[i - 1]) continue;
        for (int j = i + 1; j < n - 2; j++) {
            if (j > i + 1 && nums[j] == nums[j - 1]) continue;
            int left = j + 1, right = n - 1;
            while (left < right) {
                long sum = (long) nums[i] + nums[j] + nums[left] + nums[right];
                if (sum == target) {
                    ans.add(Arrays.asList(nums[i], nums[j], nums[left], nums[right]));
                    int l = nums[left], r = nums[right];
                    while (left < right && nums[left] == l) left++;
                    while (left < right && nums[right] == r) right--;
                } else if (sum < target) left++;
                else right--;
            }
        }
    }
    return ans;
}
```

## Complexity
Time O(n³), space O(1) auxiliary excluding output.

## Interview Point
Use `long` for the sum to avoid integer overflow.