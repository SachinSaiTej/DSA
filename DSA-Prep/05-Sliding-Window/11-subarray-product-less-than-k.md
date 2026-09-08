# Subarray Product Less Than K

## Intuition
With positive numbers, expand the window and multiply. While the product is at least `k`, divide out values from the left. Every valid window ending at `r` contributes `r-l+1` subarrays.

## Java
```java
public int numSubarrayProductLessThanK(int[] nums,int k){
    if(k<=1)return 0;long p=1;int l=0,ans=0;for(int r=0;r<nums.length;r++){p*=nums[r];while(p>=k)p/=nums[l++];ans+=r-l+1;}return ans;
}
```

## Complexity
O(n) time, O(1) space.