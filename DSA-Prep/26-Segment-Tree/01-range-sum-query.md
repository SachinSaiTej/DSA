# Range Sum Query - Mutable

## Problem
Support point updates and range-sum queries on an array efficiently.

## Intuition
A segment tree stores the sum for every interval. Updating one value changes only O(log n) tree nodes; querying a range visits O(log n) relevant nodes for a standard segment tree.

## Java
```java
class NumArray {
    int n; int[] tree;
    NumArray(int[] a){ n=a.length; tree=new int[4*Math.max(1,n)]; if(n>0)build(a,1,0,n-1); }
    void build(int[]a,int p,int l,int r){if(l==r){tree[p]=a[l];return;}int m=(l+r)/2;build(a,p*2,l,m);build(a,p*2+1,m+1,r);tree[p]=tree[p*2]+tree[p*2+1];}
    void update(int p,int l,int r,int i,int v){if(l==r){tree[p]=v;return;}int m=(l+r)/2;if(i<=m)update(p*2,l,m,i,v);else update(p*2+1,m+1,r,i,v);tree[p]=tree[p*2]+tree[p*2+1];}
    int query(int p,int l,int r,int ql,int qr){if(ql<=l&&r<=qr)return tree[p];int m=(l+r)/2,s=0;if(ql<=m)s+=query(p*2,l,m,ql,qr);if(qr>m)s+=query(p*2+1,m+1,r,ql,qr);return s;}
    public void update(int i,int v){update(1,0,n-1,i,v);}
    public int sumRange(int l,int r){return query(1,0,n-1,l,r);}
}
```

## Complexity
Build O(n), update/query O(log n), space O(n).