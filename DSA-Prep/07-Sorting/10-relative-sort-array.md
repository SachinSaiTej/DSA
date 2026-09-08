# Relative Sort Array

## Intuition
Count occurrences of each value. Emit values in the order given by `arr2`, then emit remaining values in ascending order.

## Java
```java
public int[] relativeSortArray(int[]a,int[]b){Map<Integer,Integer>f=new HashMap<>();for(int x:a)f.merge(x,1,Integer::sum);int k=0;int[]o=new int[a.length];for(int x:b)while(f.getOrDefault(x,0)>0){o[k++]=x;f.put(x,f.get(x)-1);}List<Integer>rest=new ArrayList<>();for(var e:f.entrySet())for(int i=0;i<e.getValue();i++)rest.add(e.getKey());Collections.sort(rest);for(int x:rest)o[k++]=x;return o;}
```

## Complexity
O(n log n) time, O(n) space.