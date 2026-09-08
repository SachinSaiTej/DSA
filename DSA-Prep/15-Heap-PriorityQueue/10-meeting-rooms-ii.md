# Meeting Rooms II

## Problem
Find the minimum number of meeting rooms required for all intervals.

## Intuition
Sort meetings by start time and keep a min-heap of end times. If the earliest room is free, reuse it; otherwise allocate another room.

## Java
```java
public int minMeetingRooms(int[][]a){Arrays.sort(a,(x,y)->Integer.compare(x[0],y[0]));PriorityQueue<Integer>q=new PriorityQueue<>();int best=0;for(int[]x:a){while(!q.isEmpty()&&q.peek()<=x[0])q.poll();q.offer(x[1]);best=Math.max(best,q.size());}return best;}
```

## Complexity
O(n log n) time and O(n) space.