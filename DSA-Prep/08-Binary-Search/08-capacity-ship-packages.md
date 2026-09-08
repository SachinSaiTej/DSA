# Capacity to Ship Packages

## Intuition
Binary-search the ship capacity. Greedily load packages in order and count how many days a candidate capacity needs.

## Java
```java
public int shipWithinDays(int[]w,int days){int l=0,r=0;for(int x:w){l=Math.max(l,x);r+=x;}while(l<r){int c=l+(r-l)/2,d=1,load=0;for(int x:w){if(load+x>c){d++;load=0;}load+=x;}if(d<=days)r=c;else l=c+1;}return l;}
```

## Complexity
O(n log(sum)) time, O(1) space.