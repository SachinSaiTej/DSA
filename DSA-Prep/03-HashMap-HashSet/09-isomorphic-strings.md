# Isomorphic Strings

## Problem
Determine whether two strings can be transformed into each other by a one-to-one character mapping.

## Intuition
Maintain mappings in both directions. This prevents two different characters from mapping to the same character.

## Java
```java
public boolean isIsomorphic(String s, String t) {
    if (s.length() != t.length()) return false;
    Map<Character, Character> a = new HashMap<>(), b = new HashMap<>();
    for (int i = 0; i < s.length(); i++) {
        char x=s.charAt(i), y=t.charAt(i);
        if ((a.containsKey(x) && a.get(x) != y) || (b.containsKey(y) && b.get(y) != x)) return false;
        a.put(x,y); b.put(y,x);
    }
    return true;
}
```

## Complexity
Time O(n), space O(k).