# Longest Ones

## Intuition
Treat zeroes as the limited resource. Keep a window with at most `k` zeroes; when it exceeds k, move the left edge.

## Java
```java
public int longestOnes(int[] nums,int k){
    int l=0,zeros=0,best=0;for(int r=0;r<nums.length;r++){if(nums[r]==0)zeros++;while(zeros>k)if(nums[l++]==0)zeros--;best=Math.max(best,r-l+1);}return best;
}
```

## Complexity
O(n) time, O(1) space.