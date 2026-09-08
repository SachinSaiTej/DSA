# Meeting Rooms II

## Problem
Find the minimum number of meeting rooms required for all intervals.

## Intuition
Sort start and end times separately. If the next meeting starts before the earliest current meeting ends, a new room is needed. Otherwise, a room becomes free and can be reused.

## Java
```java
public int minMeetingRooms(int[][] a){
    int n=a.length;
    if(n==0)return 0;
    int[] s=new int[n],e=new int[n];
    for(int i=0;i<n;i++){s[i]=a[i][0];e[i]=a[i][1];}
    Arrays.sort(s);Arrays.sort(e);
    int i=0,j=0,rooms=0,best=0;
    while(i<n){
        if(s[i]<e[j]){rooms++;best=Math.max(best,rooms);i++;}
        else{rooms--;j++;}
    }
    return best;
}
```

## Complexity
Time O(n log n), space O(n).