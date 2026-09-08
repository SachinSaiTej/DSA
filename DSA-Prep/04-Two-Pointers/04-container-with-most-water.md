# Container With Most Water

## Problem
Find two vertical lines that form a container holding the maximum amount of water.

## Intuition
Start at both ends. The area is limited by the shorter line, so after calculating the area, move the pointer at the shorter line inward.

## Java
```java
public int maxArea(int[] h){
    int l=0,r=h.length-1,best=0;
    while(l<r){
        best=Math.max(best,Math.min(h[l],h[r])*(r-l));
        if(h[l]<h[r])l++;else r--;
    }
    return best;
}
```

## Complexity
Time O(n), space O(1).