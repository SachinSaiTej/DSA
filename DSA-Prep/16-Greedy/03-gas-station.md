# Gas Station

## Problem
Given gas available and travel cost at each station, find the starting station that completes the circuit, or return -1.

## Intuition
If total gas is less than total cost, impossible. Otherwise, when the running tank becomes negative, none of the stations in the current segment can be a valid start; restart after that segment.

## Java
```java
public int canCompleteCircuit(int[] gas, int[] cost) {
    int total = 0, tank = 0, start = 0;
    for (int i = 0; i < gas.length; i++) {
        int gain = gas[i] - cost[i];
        total += gain; tank += gain;
        if (tank < 0) { start = i + 1; tank = 0; }
    }
    return total >= 0 ? start : -1;
}
```

## Complexity
Time O(n), space O(1).