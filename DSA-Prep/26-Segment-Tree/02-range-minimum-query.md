# Range Minimum Query

## Problem
Support range-minimum queries on an array efficiently.

## Intuition
A segment tree stores the minimum for each interval. A query combines the relevant child intervals with `min`.

## Java
```java
class SegmentTreeMin{
    int n;int[]t;
    SegmentTreeMin(int[]a){n=a.length;t=new int[4*n];build(a,1,0,n-1);}
    void build(int[]a,int p,int l,int r){if(l==r){t[p]=a[l];return;}int m=(l+r)/2;build(a,p*2,l,m);build(a,p*2+1,m+1,r);t[p]=Math.min(t[p*2],t[p*2+1]);}
    int query(int p,int l,int r,int ql,int qr){if(qr<l||r<ql)return Integer.MAX_VALUE;if(ql<=l&&r<=qr)return t[p];int m=(l+r)/2;return Math.min(query(p*2,l,m,ql,qr),query(p*2+1,m+1,r,ql,qr));}
    int query(int l,int r){return query(1,0,n-1,l,r);}
}
```

## Complexity
Build O(n), each query O(log n), space O(n).