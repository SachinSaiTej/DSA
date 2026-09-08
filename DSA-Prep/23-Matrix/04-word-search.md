# Word Search

## Problem
Determine whether a word can be formed by sequentially adjacent cells in a board without reusing a cell.

## Intuition
Start DFS from every cell matching the first character. Mark the current cell visited, explore four directions, then restore it during backtracking.

## Java
```java
public boolean exist(char[][] b,String w){
    for(int r=0;r<b.length;r++) for(int c=0;c<b[0].length;c++)
        if(dfs(b,w,r,c,0)) return true;
    return false;
}
private boolean dfs(char[][]b,String w,int r,int c,int i){
    if(i==w.length()) return true;
    if(r<0||c<0||r==b.length||c==b[0].length||b[r][c]!=w.charAt(i)) return false;
    char ch=b[r][c]; b[r][c]='#';
    boolean ok=dfs(b,w,r+1,c,i+1)||dfs(b,w,r-1,c,i+1)||dfs(b,w,r,c+1,i+1)||dfs(b,w,r,c-1,i+1);
    b[r][c]=ch; return ok;
}
```

## Complexity
Worst case O(RC·4^L), space O(L).