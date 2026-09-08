# Word Ladder

## Problem
Transform `beginWord` into `endWord` by changing one character at a time, with every intermediate word in the dictionary. Return the shortest transformation length.

## Intuition
Every word is a graph node; edges connect words differing by one character. BFS guarantees the shortest path.

## Java
```java
public int ladderLength(String begin,String end,List<String> words){
    Set<String>set=new HashSet<>(words);if(!set.contains(end))return 0;Queue<String>q=new ArrayDeque<>();q.offer(begin);int level=1;
    while(!q.isEmpty()){for(int sz=q.size();sz>0;sz--){char[]a=q.poll().toCharArray();for(int i=0;i<a.length;i++){char old=a[i];for(char c='a';c<='z';c++){if(c==old)continue;a[i]=c;String s=new String(a);if(s.equals(end))return level+1;if(set.remove(s))q.offer(s);}a[i]=old;}}level++;}return 0;
}
```

## Complexity
Time O(N·L·26), space O(N), where N is dictionary size and L word length.