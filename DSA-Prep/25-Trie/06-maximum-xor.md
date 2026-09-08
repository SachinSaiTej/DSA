# Maximum XOR for Two Numbers

## Problem
Find the maximum XOR value obtainable from two numbers in an array.

## Intuition
A bitwise Trie stores numbers by binary bits. For each number, greedily choose the opposite bit at every position because that maximizes the XOR from the most significant bit downward.

## Java
```java
static class BitNode{BitNode[]c=new BitNode[2];}
public int findMaximumXOR(int[] nums){
    BitNode root=new BitNode();for(int x:nums)insert(root,x);int best=0;
    for(int x:nums){BitNode n=root;int cur=0;for(int b=31;b>=0;b--){int bit=(x>>>b)&1,want=bit^1;if(n.c[want]!=null){cur|=1<<b;n=n.c[want];}else n=n.c[bit];}best=Math.max(best,cur);}return best;
}
void insert(BitNode n,int x){for(int b=31;b>=0;b--){int bit=(x>>>b)&1;if(n.c[bit]==null)n.c[bit]=new BitNode();n=n.c[bit];}}
```

## Complexity
Time O(32n), space O(32n).