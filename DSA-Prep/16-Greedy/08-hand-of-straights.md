# Hand of Straights

## Problem
Determine whether cards can be rearranged into groups of consecutive cards of size `groupSize`.

## Intuition
Always start with the smallest remaining card. If it occurs `count` times, those copies force the next `groupSize-1` consecutive values to occur at least as many times.

## Java
```java
public boolean isNStraightHand(int[]h,int k){if(h.length%k!=0)return false;TreeMap<Integer,Integer>m=new TreeMap<>();for(int x:h)m.merge(x,1,Integer::sum);while(!m.isEmpty()){int first=m.firstKey(),cnt=m.get(first);for(int x=first;x<first+k;x++){int c=m.getOrDefault(x,0);if(c<cnt)return false;if(c==cnt)m.remove(x);else m.put(x,c-cnt);}}return true;}
```

## Complexity
O(n log n) time and O(n) space.