# Assign Cookies

## Problem
Maximize the number of children satisfied when each child has a greed factor and each cookie has a size.

## Intuition
Sort both arrays. Give the smallest cookie that can satisfy the least greedy remaining child. If a cookie is too small, it cannot satisfy that child, so move to the next larger cookie.

## Java
```java
public int findContentChildren(int[] g,int[] s){
    Arrays.sort(g);Arrays.sort(s);int i=0,j=0;
    while(i<g.length&&j<s.length){
        if(s[j]>=g[i])i++;
        j++;
    }
    return i;
}
```

## Complexity
Time O(n log n + m log m), space O(1) apart from sorting.