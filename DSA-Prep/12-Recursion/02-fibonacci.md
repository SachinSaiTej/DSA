# Fibonacci

## Intuition
Each term is the sum of the previous two: `F(n)=F(n-1)+F(n-2)`, with `F(0)=0,F(1)=1`.

## Java
```java
int fib(int n){if(n<=1)return n;return fib(n-1)+fib(n-2);}
```

## Complexity
Naive recursion is O(2^n) time and O(n) stack. Memoization reduces time to O(n).