# Word Search II

## Problem
Find all dictionary words that can be formed by adjacent cells in a character board.

## Intuition
Build a Trie from the words, then DFS from each board cell while following Trie edges. Remove found words to avoid duplicates.

## Java
```java
class Solution {
    static class T { T[] c=new T[26]; String word; }
    public List<String> findWords(char[][] b,String[] words){
        T root=new T();
        for(String w:words){T n=root;for(char ch:w.toCharArray()){int i=ch-'a';if(n.c[i]==null)n.c[i]=new T();n=n.c[i];}n.word=w;}
        List<String> ans=new ArrayList<>();
        for(int r=0;r<b.length;r++)for(int c=0;c<b[0].length;c++)dfs(b,r,c,root,ans);
        return ans;
    }
    void dfs(char[][]b,int r,int c,T n,List<String>a){
        if(r<0||c<0||r==b.length||c==b[0].length||b[r][c]=='#')return;
        T next=n.c[b[r][c]-'a'];if(next==null)return;
        if(next.word!=null){a.add(next.word);next.word=null;}
        char old=b[r][c];b[r][c]='#';dfs(b,r+1,c,next,a);dfs(b,r-1,c,next,a);dfs(b,r,c+1,next,a);dfs(b,r,c-1,next,a);b[r][c]=old;
    }
}
```

## Complexity
O(board cells × explored trie paths) in the worst case; trie uses O(total word characters).