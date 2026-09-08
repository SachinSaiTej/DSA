# Factorial

## Problem
Compute `n!` using recursion.

## Intuition
`n! = n × (n-1)!`, with base case `0! = 1`.

## Java
```java
long factorial(int n){if(n<=1)return 1;return n*factorial(n-1);}
```

## Complexity
O(n) time and O(n) call stack.