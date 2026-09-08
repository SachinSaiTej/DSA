# Replace Words

## Problem
Replace words in a sentence by their shortest matching root from a dictionary.

## Intuition
Insert all roots into a Trie. For each word, walk the Trie until reaching a terminal root or a missing edge. The first terminal node gives the shortest root.

## Java
```java
public String replaceWords(List<String> dict,String sentence){
    Node root=new Node();for(String w:dict)insert(root,w);StringBuilder out=new StringBuilder();
    for(String w:sentence.split(" ")){if(out.length()>0)out.append(' ');out.append(find(root,w));}return out.toString();
}
static class Node{Node[]c=new Node[26];boolean end;}
void insert(Node n,String w){for(char ch:w.toCharArray()){int i=ch-'a';if(n.c[i]==null)n.c[i]=new Node();n=n.c[i];}n.end=true;}
String find(Node n,String w){StringBuilder s=new StringBuilder();for(char ch:w.toCharArray()){if(n.end)break;int i=ch-'a';if(n.c[i]==null)return w;s.append(ch);n=n.c[i];}return n.end?s.toString():w;}
```

## Complexity
Time O(total dictionary characters + sentence characters), space O(total dictionary characters).