# Maximum Average Subarray I

## Intuition
For a fixed-size window, maintain its sum incrementally: add the new right value and remove the old left value.

## Java
```java
public double findMaxAverage(int[] nums,int k){
    long sum=0;
    for(int i=0;i<k;i++)sum+=nums[i];
    long best=sum;
    for(int i=k;i<nums.length;i++){sum+=nums[i]-nums[i-k];best=Math.max(best,sum);}
    return (double)best/k;
}
```

## Complexity
O(n) time, O(1) space.