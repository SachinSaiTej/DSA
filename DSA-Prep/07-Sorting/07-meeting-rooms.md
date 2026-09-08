# Meeting Rooms

## Intuition
Sort intervals by start time. If any meeting starts before the previous meeting ends, there is a conflict.

## Java
```java
public boolean canAttendMeetings(int[][]a){Arrays.sort(a,(x,y)->Integer.compare(x[0],y[0]));for(int i=1;i<a.length;i++)if(a[i][0]<a[i-1][1])return false;return true;}
```

## Complexity
O(n log n) time, O(1) extra space apart from sorting.