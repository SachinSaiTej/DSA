# Implement Trie

## Problem
Implement a prefix tree supporting insert, exact search, and prefix search.

## Intuition
Each character corresponds to an edge. A boolean at a node marks the end of a complete word.

## Java
```java
class Trie {
    static class Node { Node[] child=new Node[26]; boolean end; }
    Node root=new Node();
    public void insert(String word){Node n=root;for(char c:word.toCharArray()){int i=c-'a';if(n.child[i]==null)n.child[i]=new Node();n=n.child[i];}n.end=true;}
    private Node find(String s){Node n=root;for(char c:s.toCharArray()){n=n.child[c-'a'];if(n==null)return null;}return n;}
    public boolean search(String w){Node n=find(w);return n!=null&&n.end;}
    public boolean startsWith(String p){return find(p)!=null;}
}
```

## Complexity
Insert/search/prefix O(L), where L is word/prefix length. Space O(total characters).