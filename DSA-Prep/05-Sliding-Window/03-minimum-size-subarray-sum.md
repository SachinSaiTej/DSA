# Minimum Size Subarray Sum

## Intuition
With positive numbers, expand the right edge until the sum reaches the target, then shrink from the left while it remains valid.

## Java
```java
public int minSubArrayLen(int target,int[] nums){
    int l=0,best=Integer.MAX_VALUE;long sum=0;
    for(int r=0;r<nums.length;r++){sum+=nums[r];while(sum>=target){best=Math.min(best,r-l+1);sum-=nums[l++];}}
    return best==Integer.MAX_VALUE?0:best;
}
```

## Complexity
O(n) time, O(1) space.