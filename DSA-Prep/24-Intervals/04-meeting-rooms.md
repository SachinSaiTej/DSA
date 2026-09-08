# Meeting Rooms

## Problem
Determine whether a person can attend all meetings represented by intervals.

## Intuition
Sort meetings by start time. If a meeting starts before the previous meeting ends, they overlap.

## Java
```java
public boolean canAttendMeetings(int[][] a){
    Arrays.sort(a,(x,y)->Integer.compare(x[0],y[0]));
    for(int i=1;i<a.length;i++)if(a[i][0]<a[i-1][1])return false;
    return true;
}
```

## Complexity
Time O(n log n), space O(1) apart from sorting.