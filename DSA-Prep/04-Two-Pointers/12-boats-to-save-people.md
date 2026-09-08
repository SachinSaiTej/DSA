# Boats to Save People

## Problem
Each boat carries at most two people and has a weight limit. Find the minimum number of boats needed.

## Intuition
Sort weights. Pair the lightest person with the heaviest whenever they fit. If they do not fit, the heaviest must go alone.

## Java
```java
public int numRescueBoats(int[] people,int limit){
    Arrays.sort(people);int l=0,r=people.length-1,boats=0;
    while(l<=r){
        if(people[l]+people[r]<=limit)l++;
        r--;boats++;
    }
    return boats;
}
```

## Complexity
Time O(n log n), space O(1) apart from sorting.