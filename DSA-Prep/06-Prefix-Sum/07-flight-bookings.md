# Corporate Flight Bookings

## Intuition
Use a difference array: add bookings at the start and subtract after the end. A prefix sum then reconstructs seats booked at every flight.

## Java
```java
public int[] corpFlightBookings(int[][] b,int n){int[] d=new int[n+1];for(int[] x:b){d[x[0]-1]+=x[2];d[x[1]]-=x[2];}int[] ans=new int[n];int cur=0;for(int i=0;i<n;i++){cur+=d[i];ans[i]=cur;}return ans;}
```

## Complexity
O(n + bookings) time, O(n) space.