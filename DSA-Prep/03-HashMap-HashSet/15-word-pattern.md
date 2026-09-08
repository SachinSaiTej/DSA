# Word Pattern

## Problem
Determine whether a string follows a pattern where each pattern character maps to exactly one word and vice versa.

## Intuition
This is the same one-to-one mapping idea as isomorphic strings. Maintain maps in both directions so no two pattern characters share a word and no word maps to two characters.

## Java
```java
public boolean wordPattern(String pattern, String s) {
    String[] words=s.split(" ");
    if(words.length!=pattern.length()) return false;
    Map<Character,String> pToW=new HashMap<>();
    Map<String,Character> wToP=new HashMap<>();
    for(int i=0;i<pattern.length();i++){
        char p=pattern.charAt(i); String w=words[i];
        if((pToW.containsKey(p)&&!pToW.get(p).equals(w)) || (wToP.containsKey(w)&&wToP.get(w)!=p)) return false;
        pToW.put(p,w); wToP.put(w,p);
    }
    return true;
}
```

## Complexity
Time O(n), space O(n).