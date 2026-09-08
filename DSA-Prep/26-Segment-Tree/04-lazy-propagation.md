# Lazy Propagation

## Problem
Support range updates and range-sum queries efficiently.

## Intuition
Instead of immediately pushing a range update to every leaf, store a pending update at the segment node. Push it to children only when their values are needed.

## Java
```java
void update(int p,int l,int r,int ql,int qr,int val){
    if(qr<l||r<ql)return;
    if(ql<=l&&r<=qr){tree[p]+=val*(r-l+1);lazy[p]+=val;return;}
    push(p,l,r);int m=(l+r)/2;update(p*2,l,m,ql,qr,val);update(p*2+1,m+1,r,ql,qr,val);tree[p]=tree[p*2]+tree[p*2+1];
}
int query(int p,int l,int r,int ql,int qr){
    if(qr<l||r<ql)return 0;if(ql<=l&&r<=qr)return tree[p];push(p,l,r);int m=(l+r)/2;return query(p*2,l,m,ql,qr)+query(p*2+1,m+1,r,ql,qr);
}
void push(int p,int l,int r){if(l==r||lazy[p]==0)return;int m=(l+r)/2,v=lazy[p];tree[p*2]+=v*(m-l+1);tree[p*2+1]+=v*(r-m);lazy[p*2]+=v;lazy[p*2+1]+=v;lazy[p]=0;}
```

## Complexity
Range update and query O(log n), space O(n).