# Gas Station

## Problem
Given gas available and travel cost at each station, find a starting station that lets you complete the circular route once, or return `-1` if impossible.

## Intuition
If total gas is less than total cost, the circuit is impossible. While scanning, if the current tank becomes negative, every station from the current start through this station is an invalid start, so restart at the next station.

## Java
```java
public int canCompleteCircuit(int[] gas, int[] cost) {
    int total = 0, tank = 0, start = 0;
    for (int i = 0; i < gas.length; i++) {
        int gain = gas[i] - cost[i];
        total += gain;
        tank += gain;
        if (tank < 0) {
            start = i + 1;
            tank = 0;
        }
    }
    return total >= 0 ? start : -1;
}
```

## Complexity
Time O(n), space O(1).