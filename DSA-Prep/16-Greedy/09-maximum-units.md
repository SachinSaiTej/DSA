# Maximum Units on a Truck

## Intuition
Sort box types by units per box descending. Always load the boxes with the highest value first until truck capacity is full.

## Java
```java
public int maximumUnits(int[][]b,int size){Arrays.sort(b,(x,y)->Integer.compare(y[1],x[1]));int ans=0;for(int[]x:b){int take=Math.min(size,x[0]);ans+=take*x[1];size-=take;if(size==0)break;}return ans;}
```

## Complexity
O(n log n) time and O(1) extra space.