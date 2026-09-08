# Boats to Save People

## Problem
Each boat can carry at most two people and has a maximum weight limit. Return the minimum number of boats needed.

## Intuition
Sort the people by weight. Pair the lightest person with the heaviest person whenever they fit. If they do not fit, the heaviest person must travel alone.

## Java
```java
public int numRescueBoats(int[] people, int limit) {
    Arrays.sort(people);
    int left = 0, right = people.length - 1, boats = 0;
    while (left <= right) {
        if (people[left] + people[right] <= limit) left++;
        right--;
        boats++;
    }
    return boats;
}
```

## Complexity
Time O(n log n), space O(1) apart from sorting.