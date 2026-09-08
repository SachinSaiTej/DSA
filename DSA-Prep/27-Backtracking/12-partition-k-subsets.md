# Partition to K Equal Sum Subsets

## Problem
Determine whether an array can be partitioned into k non-empty subsets having equal sums.

## Intuition
The total must be divisible by k. Sort descending and place each number into a bucket whose current sum does not exceed the target, backtracking when needed.

## Java
```java
public boolean canPartitionKSubsets(int[]a,int k){int sum=0;for(int x:a)sum+=x;if(k<=0||sum%k!=0)return false;Arrays.sort(a);reverse(a);if(a[0]>sum/k)return false;return dfs(a,0,new int[k],sum/k);}
void reverse(int[]a){for(int l=0,r=a.length-1;l<r;l++,r--){int t=a[l];a[l]=a[r];a[r]=t;}}
boolean dfs(int[]a,int i,int[]b,int target){if(i==a.length)return true;for(int j=0;j<b.length;j++){if(j>0&&b[j]==b[j-1])continue;if(b[j]+a[i]>target)continue;b[j]+=a[i];if(dfs(a,i+1,b,target))return true;b[j]-=a[i];if(b[j]==0)break;}return false;}
```

## Complexity
Worst-case exponential; space O(k+n).