# Merge Intervals

## Intuition
Sort by start time. Merge when the next interval overlaps the current one; otherwise emit the current interval.

## Java
```java
public int[][] merge(int[][]a){Arrays.sort(a,(x,y)->Integer.compare(x[0],y[0]));List<int[]>o=new ArrayList<>();for(int[]x:a){if(o.isEmpty()||o.get(o.size()-1)[1]<x[0])o.add(x.clone());else o.get(o.size()-1)[1]=Math.max(o.get(o.size()-1)[1],x[1]);}return o.toArray(new int[0][]);}
```

## Complexity
O(n log n) time, O(n) output space.