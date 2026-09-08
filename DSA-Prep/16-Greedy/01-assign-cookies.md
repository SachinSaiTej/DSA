# Assign Cookies

## Problem
Given children with greed factors and cookies with sizes, maximize the number of children who can be satisfied. A child is satisfied when the cookie size is at least the child's greed factor.

## Intuition
Sort both arrays. Always try to satisfy the least greedy remaining child with the smallest cookie that can satisfy them. This preserves larger cookies for greedier children.

## Java
```java
public int findContentChildren(int[] g, int[] s) {
    Arrays.sort(g);
    Arrays.sort(s);
    int child = 0, cookie = 0;
    while (child < g.length && cookie < s.length) {
        if (s[cookie] >= g[child]) child++;
        cookie++;
    }
    return child;
}
```

## Complexity
Time O(n log n + m log m), space O(1) apart from sorting.