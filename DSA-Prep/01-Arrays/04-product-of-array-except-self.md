# Product of Array Except Self

## Problem
For every index, return the product of all elements except the element at that index. Do not use division.

## Intuition
For index `i`, the answer is `product of everything left × product of everything right`. Build the left product into the answer, then multiply by a running right product.

## Java
```java
public int[] productExceptSelf(int[] nums) {
    int n = nums.length;
    int[] ans = new int[n];
    Arrays.fill(ans, 1);

    int prefix = 1;
    for (int i = 0; i < n; i++) {
        ans[i] = prefix;
        prefix *= nums[i];
    }

    int suffix = 1;
    for (int i = n - 1; i >= 0; i--) {
        ans[i] *= suffix;
        suffix *= nums[i];
    }
    return ans;
}
```

## Complexity
Time O(n), extra space O(1) excluding the output array.

## Interview Point
This naturally handles zero values without special cases.