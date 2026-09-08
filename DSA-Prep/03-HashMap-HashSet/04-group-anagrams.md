# Group Anagrams

## Problem
Group strings that are anagrams of one another.

## Intuition
Anagrams have identical character-frequency signatures. Use the frequency signature as a map key.

## Java
```java
public List<List<String>> groupAnagrams(String[] strs) {
    Map<String, List<String>> groups = new HashMap<>();
    for (String s : strs) {
        int[] count = new int[26];
        for (char c : s.toCharArray()) count[c - 'a']++;
        StringBuilder key = new StringBuilder();
        for (int x : count) key.append('#').append(x);
        groups.computeIfAbsent(key.toString(), k -> new ArrayList<>()).add(s);
    }
    return new ArrayList<>(groups.values());
}
```

## Complexity
Time O(total characters), space O(total characters).