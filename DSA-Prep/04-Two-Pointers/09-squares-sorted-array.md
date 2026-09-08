# Squares of a Sorted Array

## Problem
Return the squares of a sorted integer array in sorted order.

## Intuition
The largest square must come from either the leftmost negative or rightmost positive value. Compare both ends and fill the result from right to left.

## Java
```java
public int[] sortedSquares(int[] nums){
    int[] ans=new int[nums.length];int l=0,r=nums.length-1,k=r;
    while(l<=r){
        int a=Math.abs(nums[l]),b=Math.abs(nums[r]);
        if(a>b)ans[k--]=a*a,l++;else ans[k--]=b*b,r--;
    }
    return ans;
}
```

## Complexity
Time O(n), space O(n) for output.