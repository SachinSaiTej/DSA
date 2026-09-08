# Path With Minimum Effort

## Problem
Find a path from top-left to bottom-right minimizing the maximum absolute height difference between adjacent cells.

## Intuition
Treat the effort of a path as its maximum edge cost. Dijkstra works by minimizing this bottleneck value.

## Java
```java
public int minimumEffortPath(int[][]h){
    int R=h.length,C=h[0].length;int[][]d=new int[R][C];for(int[]x:d)Arrays.fill(x,Integer.MAX_VALUE);d[0][0]=0;
    PriorityQueue<int[]>pq=new PriorityQueue<>((a,b)->a[0]-b[0]);pq.offer(new int[]{0,0,0});int[][]ds={{1,0},{-1,0},{0,1},{0,-1}};
    while(!pq.isEmpty()){int[]x=pq.poll(),e=x[0],r=x[1],c=x[2];if(e!=d[r][c])continue;if(r==R-1&&c==C-1)return e;for(int[]z:ds){int nr=r+z[0],nc=c+z[1];if(nr<0||nc<0||nr>=R||nc>=C)continue;int ne=Math.max(e,Math.abs(h[r][c]-h[nr][nc]));if(ne<d[nr][nc]){d[nr][nc]=ne;pq.offer(new int[]{ne,nr,nc});}}}return 0;
}
```

## Complexity
Time O(RC log(RC)), space O(RC).