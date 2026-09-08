# Minimum Index Sum of Two Lists

## Problem
Find common strings between two lists whose sum of indices is minimum.

## Intuition
Map every string in the first list to its index. Scan the second list and track the smallest combined index for common strings.

## Java
```java
public String[] findRestaurant(String[] list1, String[] list2) {
    Map<String,Integer> index=new HashMap<>();
    for(int i=0;i<list1.length;i++) index.put(list1[i],i);
    List<String> ans=new ArrayList<>(); int best=Integer.MAX_VALUE;
    for(int j=0;j<list2.length;j++) if(index.containsKey(list2[j])){
        int sum=j+index.get(list2[j]);
        if(sum<best){best=sum;ans.clear();ans.add(list2[j]);}
        else if(sum==best) ans.add(list2[j]);
    }
    return ans.toArray(new String[0]);
}
```

## Complexity
Time O(n + m), space O(n).