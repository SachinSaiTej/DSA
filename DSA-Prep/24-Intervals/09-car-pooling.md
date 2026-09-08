# Car Pooling

## Problem
Determine whether all passengers can be transported without exceeding vehicle capacity, given pickup/drop-off intervals.

## Intuition
Use a difference array: add passengers at pickup and subtract them at drop-off. A prefix sum gives passengers currently in the car.

## Java
```java
public boolean carPooling(int[][] trips,int capacity){
    int[]d=new int[1001];for(int[]t:trips){d[t[1]]+=t[0];d[t[2]]-=t[0];}
    int cur=0;for(int x:d){cur+=x;if(cur>capacity)return false;}return true;
}
```

## Complexity
Time O(n + maxLocation), space O(maxLocation).