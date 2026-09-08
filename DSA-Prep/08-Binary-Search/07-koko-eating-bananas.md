# Koko Eating Bananas

## Intuition
Binary-search the eating speed. For a candidate speed, calculate required hours using ceiling division. If it fits, try slower.

## Java
```java
public int minEatingSpeed(int[]p,int h){int l=1,r=0;for(int x:p)r=Math.max(r,x);while(l<r){int m=l+(r-l)/2;long hours=0;for(int x:p)hours+=(x+m-1)/m;if(hours<=h)r=m;else l=m+1;}return l;}
```

## Complexity
O(n log maxPile) time, O(1) space.