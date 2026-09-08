# N-Queens

## Problem
Place n queens on an n×n chessboard so no two queens attack each other.

## Intuition
Place one queen per row. Track occupied columns and diagonals so invalid positions are rejected in O(1).

## Java
```java
public List<List<String>> solveNQueens(int n){List<List<String>>ans=new ArrayList<>();boolean[]col=new boolean[n],d1=new boolean[2*n],d2=new boolean[2*n];char[][]b=new char[n][n];for(char[]r:b)Arrays.fill(r,'.');dfs(0,b,col,d1,d2,ans);return ans;}
void dfs(int r,char[][]b,boolean[]c,boolean[]d1,boolean[]d2,List<List<String>>a){if(r==b.length){List<String>x=new ArrayList<>();for(char[]row:b)x.add(new String(row));a.add(x);return;}for(int j=0;j<b.length;j++){int x=r-j+b.length,y=r+j;if(c[j]||d1[x]||d2[y])continue;c[j]=d1[x]=d2[y]=true;b[r][j]='Q';dfs(r+1,b,c,d1,d2,a);b[r][j]='.';c[j]=d1[x]=d2[y]=false;}}
```

## Complexity
Worst-case O(n!), space O(n²) for the board and output.