# Find the Duplicate Number

## Problem
An array of `n + 1` integers contains values in `[1,n]`. Find the duplicated value without modifying the array and using O(1) extra space.

## Intuition
Treat each value as a pointer to another index. Because there are `n+1` values in `n` possible positions, a cycle must exist. Floyd's cycle detection finds the cycle entry, which is the duplicate.

## Java
```java
public int findDuplicate(int[] nums) {
    int slow = nums[0], fast = nums[0];
    do {
        slow = nums[slow];
        fast = nums[nums[fast]];
    } while (slow != fast);

    slow = nums[0];
    while (slow != fast) {
        slow = nums[slow];
        fast = nums[fast];
    }
    return slow;
}
```

## Complexity
Time O(n), space O(1).

## Interview Point
This is the same mathematical idea as detecting the entrance of a linked-list cycle.