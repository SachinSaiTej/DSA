# Segment Tree Construction

## Problem
Build a segment tree that represents an array and supports interval aggregation.

## Intuition
Recursively split the range into halves. A leaf represents one array element; each internal node combines its two children.

## Java
```java
class SegmentTree{
    int[] tree;int n;
    SegmentTree(int[]a){n=a.length;tree=new int[4*n];build(a,1,0,n-1);}
    void build(int[]a,int p,int l,int r){if(l==r){tree[p]=a[l];return;}int m=(l+r)/2;build(a,p*2,l,m);build(a,p*2+1,m+1,r);tree[p]=tree[p*2]+tree[p*2+1];}
}
```

## Complexity
Construction O(n), space O(n).