# Design Add and Search Words Data Structure

## Problem
Implement `addWord` and `search`, where search supports `.` matching any single character.

## Intuition
A Trie handles normal characters directly. When `.` appears, try every possible child recursively.

## Java
```java
class WordDictionary {
    static class Node{Node[]c=new Node[26];boolean end;}
    Node root=new Node();
    public void addWord(String w){Node n=root;for(char ch:w.toCharArray()){int i=ch-'a';if(n.c[i]==null)n.c[i]=new Node();n=n.c[i];}n.end=true;}
    public boolean search(String w){return dfs(root,w,0);}
    boolean dfs(Node n,String w,int i){if(n==null)return false;if(i==w.length())return n.end;char ch=w.charAt(i);if(ch=='.'){for(Node x:n.c)if(dfs(x,w,i+1))return true;return false;}return dfs(n.c[ch-'a'],w,i+1);}
}
```

## Complexity
Insert O(L). Search O(26^L) worst case with wildcards, typically much smaller.