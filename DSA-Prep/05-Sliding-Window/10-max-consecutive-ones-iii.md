# Max Consecutive Ones III

## Intuition
Use a sliding window containing at most `k` zeroes. The longest valid window is the answer.

## Java
```java
public int longestOnes(int[] nums,int k){
    int l=0,z=0,best=0;for(int r=0;r<nums.length;r++){z+=nums[r]==0?1:0;while(z>k)z-=nums[l++]==0?1:0;best=Math.max(best,r-l+1);}return best;
}
```

## Complexity
O(n) time, O(1) space.