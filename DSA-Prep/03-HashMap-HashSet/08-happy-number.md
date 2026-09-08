# Happy Number

## Problem
Repeatedly replace a number by the sum of the squares of its digits. Determine whether it eventually reaches 1.

## Intuition
The process either reaches 1 or enters a cycle. A `HashSet` records previously seen numbers; seeing one again means a cycle.

## Java
```java
public boolean isHappy(int n) {
    Set<Integer> seen = new HashSet<>();
    while (n != 1 && seen.add(n)) {
        int sum = 0;
        while (n > 0) { int d = n % 10; sum += d * d; n /= 10; }
        n = sum;
    }
    return n == 1;
}
```

## Complexity
Time O(log n) per generated state; space O(number of states).