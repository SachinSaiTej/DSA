# Trapping Rain Water

## Problem
Given bar heights, calculate how much water can be trapped after raining.

## Intuition
For each position, water depends on the smaller of the tallest wall on its left and right. Two pointers let us maintain those boundaries without extra arrays.

## Java
```java
public int trap(int[] height) {
    int left = 0, right = height.length - 1;
    int leftMax = 0, rightMax = 0, water = 0;

    while (left < right) {
        if (height[left] <= height[right]) {
            if (height[left] >= leftMax) leftMax = height[left];
            else water += leftMax - height[left];
            left++;
        } else {
            if (height[right] >= rightMax) rightMax = height[right];
            else water += rightMax - height[right];
            right--;
        }
    }
    return water;
}
```

## Complexity
Time O(n), space O(1).

## Key Insight
Process the side with the smaller current boundary because that side determines the maximum possible water level at that step.