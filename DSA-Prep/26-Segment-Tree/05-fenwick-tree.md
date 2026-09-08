# Fenwick Tree / BIT

## Problem
Support point updates and prefix-sum queries efficiently.

## Intuition
A Fenwick tree stores partial sums using the lowest set bit to determine the covered range. Both update and prefix sum move through O(log n) nodes.

## Java
```java
class Fenwick{
    int[]bit;int n;Fenwick(int n){this.n=n;bit=new int[n+1];}
    void add(int i,int delta){for(i++;i<=n;i+=i&-i)bit[i]+=delta;}
    int sum(int i){int s=0;for(i++;i>0;i-=i&-i)s+=bit[i];return s;}
    int rangeSum(int l,int r){return sum(r)-(l==0?0:sum(l-1));}
}
```

## Complexity
Update and query O(log n), space O(n).