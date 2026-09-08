# Matchsticks to Square

## Problem
Determine whether all matchsticks can form a square using every stick exactly once.

## Intuition
Each side must have length `sum / 4`. Sort sticks descending and place each stick into one of four sides, backtracking when a placement fails.

## Java
```java
public boolean makesquare(int[]a){int sum=0;for(int x:a)sum+=x;if(a.length<4||sum%4!=0)return false;Arrays.sort(a);reverse(a);if(a[0]>sum/4)return false;return dfs(a,0,new int[4],sum/4);}
void reverse(int[]a){for(int l=0,r=a.length-1;l<r;l++,r--){int t=a[l];a[l]=a[r];a[r]=t;}}
boolean dfs(int[]a,int i,int[]s,int target){if(i==a.length)return s[0]==target&&s[1]==target&&s[2]==target;for(int j=0;j<4;j++){if(s[j]+a[i]>target)continue;s[j]+=a[i];if(dfs(a,i+1,s,target))return true;s[j]-=a[i];if(s[j]==0)break;}return false;}
```

## Complexity
Worst-case exponential; recursion depth O(n).