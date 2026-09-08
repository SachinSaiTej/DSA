# Group Anagrams

## Problem
Group strings that are anagrams of each other.

## Intuition
Anagrams have identical character counts. Use a canonical key for each word, such as its sorted characters, and map that key to the group.

## Java
```java
public List<List<String>> groupAnagrams(String[] strs) {
    Map<String, List<String>> map = new HashMap<>();
    for (String s : strs) {
        char[] chars = s.toCharArray();
        Arrays.sort(chars);
        String key = new String(chars);
        map.computeIfAbsent(key, k -> new ArrayList<>()).add(s);
    }
    return new ArrayList<>(map.values());
}
```

## Complexity
Time O(n · k log k), where k is average word length; space O(nk).

## Interview Insight
For lowercase English letters, a 26-count frequency array can replace sorting and improve the per-word cost to O(k).