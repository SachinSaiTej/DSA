# Pow(x, n)

## Problem
Compute `x^n` efficiently, including negative exponents.

## Intuition
Exponentiation by squaring cuts the exponent in half each recursion. If `n` is even, square the result; if odd, multiply once by `x`.

## Java
```java
public double myPow(double x, int n) {
    long exp = n;
    if (exp < 0) { x = 1 / x; exp = -exp; }
    return pow(x, exp);
}
private double pow(double x, long n) {
    if (n == 0) return 1.0;
    double half = pow(x, n / 2);
    return (n % 2 == 0) ? half * half : half * half * x;
}
```

## Complexity
Time O(log n), space O(log n).