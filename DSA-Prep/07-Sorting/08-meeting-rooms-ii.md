# Meeting Rooms II

## Intuition
Sort meetings by start time and use a min-heap of end times. The heap size is the number of rooms currently required.

## Java
```java
public int minMeetingRooms(int[][]a){Arrays.sort(a,(x,y)->Integer.compare(x[0],y[0]));PriorityQueue<Integer>q=new PriorityQueue<>();for(int[]x:a){if(!q.isEmpty()&&q.peek()<=x[0])q.poll();q.offer(x[1]);}return q.size();}
```

## Complexity
O(n log n) time, O(n) space.