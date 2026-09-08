# Fruit Into Baskets

## Intuition
This is the longest subarray containing at most two distinct values. Track counts with a map and shrink when a third type appears.

## Java
```java
public int totalFruit(int[] fruits){
    Map<Integer,Integer> m=new HashMap<>();int l=0,best=0;
    for(int r=0;r<fruits.length;r++){m.merge(fruits[r],1,Integer::sum);while(m.size()>2){m.compute(fruits[l],(k,v)->v==1?null:v-1);l++;}best=Math.max(best,r-l+1);}return best;
}
```

## Complexity
O(n) time, O(1) space because at most 3 keys are tracked.