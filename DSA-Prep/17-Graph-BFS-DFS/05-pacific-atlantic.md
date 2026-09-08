# Pacific Atlantic Water Flow

## Problem
Find cells from which water can flow to both the Pacific and Atlantic oceans. Water moves from a cell to an equal or lower height.

## Intuition
Reverse the flow: start DFS from each ocean's boundary and move to neighbors of equal or greater height. Cells reached from both sides are answers.

## Java
```java
public List<List<Integer>> pacificAtlantic(int[][] h){
    int R=h.length,C=h[0].length; boolean[][] p=new boolean[R][C],a=new boolean[R][C];
    for(int r=0;r<R;r++){dfs(h,r,0,p,Integer.MIN_VALUE);dfs(h,r,C-1,a,Integer.MIN_VALUE);}
    for(int c=0;c<C;c++){dfs(h,0,c,p,Integer.MIN_VALUE);dfs(h,R-1,c,a,Integer.MIN_VALUE);}
    List<List<Integer>> ans=new ArrayList<>();
    for(int r=0;r<R;r++)for(int c=0;c<C;c++)if(p[r][c]&&a[r][c])ans.add(Arrays.asList(r,c)); return ans;
}
void dfs(int[][]h,int r,int c,boolean[][]v,int prev){
    if(r<0||c<0||r==h.length||c==h[0].length||v[r][c]||h[r][c]<prev)return;
    v[r][c]=true; dfs(h,r+1,c,v,h[r][c]);dfs(h,r-1,c,v,h[r][c]);dfs(h,r,c+1,v,h[r][c]);dfs(h,r,c-1,v,h[r][c]);
}
```

## Complexity
Time O(RC), space O(RC).