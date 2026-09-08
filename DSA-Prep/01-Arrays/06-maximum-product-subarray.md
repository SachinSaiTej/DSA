# Maximum Product Subarray

## Problem
Find the contiguous subarray with the largest product.

## Intuition
A negative number can turn the smallest negative product into the largest positive product. Track both the maximum and minimum product ending at the current index.

## Java
```java
public int maxProduct(int[] nums) {
    int max = nums[0];
    int min = nums[0];
    int answer = nums[0];

    for (int i = 1; i < nums.length; i++) {
        int x = nums[i];
        if (x < 0) {
            int temp = max;
            max = min;
            min = temp;
        }
        max = Math.max(x, max * x);
        min = Math.min(x, min * x);
        answer = Math.max(answer, max);
    }
    return answer;
}
```

## Complexity
Time O(n), space O(1).

## Key Insight
Unlike maximum sum, we need two states because multiplication by a negative value reverses the ordering.