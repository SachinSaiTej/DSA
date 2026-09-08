# K Closest Points to Origin

## Intuition
Maintain a max-heap of size k ordered by distance. If it grows beyond k, remove the farthest point currently kept.

## Java
```java
public int[][] kClosest(int[][]p,int k){PriorityQueue<int[]>q=new PriorityQueue<>((a,b)->Integer.compare(b[0]*b[0]+b[1]*b[1],a[0]*a[0]+a[1]*a[1]));for(int[]x:p){q.offer(x);if(q.size()>k)q.poll();}int[][]a=new int[k][2];for(int i=0;i<k;i++)a[i]=q.poll();return a;}
```

## Complexity
O(n log k) time and O(k) space.