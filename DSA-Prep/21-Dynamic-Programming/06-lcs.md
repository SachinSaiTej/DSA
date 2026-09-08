# Longest Common Subsequence

## Problem
Find the length of the longest subsequence common to two strings.

## Intuition
If the current characters match, extend the LCS. Otherwise skip one character from either string and take the better result.

## Java
```java
public int longestCommonSubsequence(String a,String b){int m=a.length(),n=b.length();int[][]d=new int[m+1][n+1];for(int i=1;i<=m;i++)for(int j=1;j<=n;j++)d[i][j]=a.charAt(i-1)==b.charAt(j-1)?d[i-1][j-1]+1:Math.max(d[i-1][j],d[i][j-1]);return d[m][n];}
```

## Complexity
Time O(mn), space O(mn).