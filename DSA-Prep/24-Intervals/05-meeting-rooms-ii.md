# Meeting Rooms II

## Problem
Find the minimum number of meeting rooms required for all intervals.

## Intuition
Sort start and end times separately. When the next meeting starts before the earliest current meeting ends, a new room is needed; otherwise reuse a room.

## Java
```java
public int minMeetingRooms(int[][] a){
    int n=a.length;if(n==0)return 0;int[]s=new int[n],e=new int[n];
    for(int i=0;i<n;i++){s[i]=a[i][0];e[i]=a[i][1];}
    Arrays.sort(s);Arrays.sort(e);int i=0,j=0,rooms=0;
    while(i<n){if(s[i]<e[j]){rooms++;i++;}else{i++;j--;rooms--;rooms++;}}
    return rooms;
}
```

## Complexity
Time O(n log n), space O(n).