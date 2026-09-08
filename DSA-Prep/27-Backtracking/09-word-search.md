# Word Search

## Problem
Determine whether a word can be formed by adjacent board cells without reusing a cell.

## Intuition
Run DFS from every matching starting cell. Mark a cell while exploring and restore it after the recursive call.

## Java
```java
public boolean exist(char[][]b,String w){for(int r=0;r<b.length;r++)for(int c=0;c<b[0].length;c++)if(dfs(b,w,r,c,0))return true;return false;}
boolean dfs(char[][]b,String w,int r,int c,int i){if(i==w.length())return true;if(r<0||c<0||r==b.length||c==b[0].length||b[r][c]!=w.charAt(i))return false;char x=b[r][c];b[r][c]='#';boolean ok=dfs(b,w,r+1,c,i+1)||dfs(b,w,r-1,c,i+1)||dfs(b,w,r,c+1,i+1)||dfs(b,w,r,c-1,i+1);b[r][c]=x;return ok;}
```

## Complexity
Worst case O(RC·4^L), space O(L).