# Power of X

## Problem
Compute `x^n` efficiently using recursion, including negative exponents.

## Intuition
Use exponentiation by squaring. Compute `x^(n/2)` once; square it, and multiply by `x` when the exponent is odd.

## Java
```java
public double myPow(double x,int n){long e=n;if(e<0){x=1/x;e=-e;}return power(x,e);}private double power(double x,long n){if(n==0)return 1;double h=power(x,n/2);return n%2==0?h*h:h*h*x;}
```

## Complexity
O(log n) time and O(log n) recursion space.