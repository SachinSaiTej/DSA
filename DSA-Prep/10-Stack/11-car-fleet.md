# Car Fleet

## Intuition
Sort cars by position descending. Compute each car's arrival time at the target. A slower/equal fleet ahead absorbs the current car; otherwise the current car starts a new fleet.

## Java
```java
public int carFleet(int target,int[]pos,int[]speed){Integer[]idx=new Integer[pos.length];for(int i=0;i<pos.length;i++)idx[i]=i;Arrays.sort(idx,(i,j)->Integer.compare(pos[j],pos[i]));double last=0;int fleets=0;for(int i:idx){double time=(double)(target-pos[i])/speed[i];if(time>last){fleets++;last=time;}}return fleets;}
```

## Complexity
O(n log n) time, O(n) space.