# Trapping Rain Water

## Problem
Given bar heights, compute how much rain water can be trapped.

## Intuition
Use two pointers and maintain the highest wall seen from each side. Water at a position is determined by the smaller boundary; process that side when its maximum is smaller.

## Java
```java
public int trap(int[] h){
    int l=0,r=h.length-1,leftMax=0,rightMax=0,water=0;
    while(l<r){
        if(h[l]<=h[r]){leftMax=Math.max(leftMax,h[l]);water+=leftMax-h[l];l++;}
        else{rightMax=Math.max(rightMax,h[r]);water+=rightMax-h[r];r--;}
    }
    return water;
}
```

## Complexity
Time O(n), space O(1).