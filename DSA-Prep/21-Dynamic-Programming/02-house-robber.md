# House Robber

## Problem
Maximize money robbed from houses when adjacent houses cannot both be robbed.

## Intuition
At each house, choose whether to skip it or rob it. Keep only the best values for the previous two positions.

## Java
```java
public int rob(int[] nums) {
    int prevTwo = 0;
    int prevOne = 0;

    for (int money : nums) {
        int current = Math.max(prevOne, prevTwo + money);
        prevTwo = prevOne;
        prevOne = current;
    }

    return prevOne;
}
```

## Complexity
Time O(n), space O(1).