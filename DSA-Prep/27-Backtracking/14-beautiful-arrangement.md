# Beautiful Arrangement

## Problem
Count permutations of `1..n` where for every position i, either `perm[i]` is divisible by i or i is divisible by `perm[i]`.

## Intuition
Build the permutation position by position. Track used numbers and only choose values compatible with the current position.

## Java
```java
public int countArrangement(int n){boolean[]u=new boolean[n+1];return dfs(1,n,u);}
int dfs(int pos,int n,boolean[]u){if(pos>n)return 1;int ans=0;for(int x=1;x<=n;x++)if(!u[x]&&(x%pos==0||pos%x==0)){u[x]=true;ans+=dfs(pos+1,n,u);u[x]=false;}return ans;}
```

## Complexity
Worst-case O(n!), space O(n).