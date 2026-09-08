# Rotting Oranges

## Intuition
Start BFS simultaneously from every rotten orange. Each BFS level represents one minute and rots adjacent fresh oranges.

## Java
```java
public int orangesRotting(int[][] g){
    Queue<int[]> q=new ArrayDeque<>();int fresh=0;
    for(int r=0;r<g.length;r++)for(int c=0;c<g[0].length;c++){if(g[r][c]==2)q.offer(new int[]{r,c});else if(g[r][c]==1)fresh++;}
    int time=0;int[][] d={{1,0},{-1,0},{0,1},{0,-1}};
    while(!q.isEmpty()&&fresh>0){for(int s=q.size();s>0;s--){int[] p=q.poll();for(int[] x:d){int r=p[0]+x[0],c=p[1]+x[1];if(r>=0&&c>=0&&r<g.length&&c<g[0].length&&g[r][c]==1){g[r][c]=2;fresh--;q.offer(new int[]{r,c});}}}time++;}
    return fresh==0?time:-1;
}
```

## Complexity
O(RC) time and O(RC) space.