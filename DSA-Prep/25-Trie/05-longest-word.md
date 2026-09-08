# Longest Word in Dictionary

## Problem
Find the longest word that can be built one character at a time, with every prefix also present in the dictionary. Break ties lexicographically smallest.

## Intuition
Insert words into a Trie and DFS only through terminal nodes. Since a word is valid only when all its prefixes exist, we can build candidates character by character.

## Java
```java
public String longestWord(String[] words){
    Arrays.sort(words);Node root=new Node();for(String w:words)insert(root,w);return dfs(root,new StringBuilder());
}
static class Node{Node[]c=new Node[26];String word;}
void insert(Node n,String w){for(char ch:w.toCharArray()){int i=ch-'a';if(n.c[i]==null)n.c[i]=new Node();n=n.c[i];}n.word=w;}
String dfs(Node n,StringBuilder cur){String best=n.word==null?"":n.word;for(int i=0;i<26;i++)if(n.c[i]!=null&&n.c[i].word!=null){String x=dfs(n.c[i],cur);if(x.length()>best.length()||(x.length()==best.length()&&!x.isEmpty()&&x.compareTo(best)<0))best=x;}return best;}
```

## Complexity
O(total characters + trie nodes), space O(total characters).