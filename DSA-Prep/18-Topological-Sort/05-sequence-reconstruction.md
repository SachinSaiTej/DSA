# Sequence Reconstruction

## Problem
Determine whether an original sequence can be uniquely reconstructed from a collection of subsequences.

## Intuition
Build the prerequisite graph and perform topological BFS. Uniqueness requires exactly one available node at every step.

## Java
```java
public boolean sequenceReconstruction(int[] org,List<List<Integer>> seqs){
    Map<Integer,Set<Integer>>g=new HashMap<>();Map<Integer,Integer>in=new HashMap<>();
    for(int x:org){g.put(x,new HashSet<>());in.put(x,0);}
    for(List<Integer>s:seqs)for(int x:s)if(!g.containsKey(x))return false;
    for(List<Integer>s:seqs)for(int i=1;i<s.size();i++){int a=s.get(i-1),b=s.get(i);if(g.get(a).add(b))in.put(b,in.get(b)+1);}
    Queue<Integer>q=new ArrayDeque<>();for(int x:org)if(in.get(x)==0)q.offer(x);int k=0;
    while(!q.isEmpty()){
        if(q.size()!=1)return false;int u=q.poll();if(k==org.length||u!=org[k++])return false;
        for(int v:g.get(u)){int d=in.get(v)-1;in.put(v,d);if(d==0)q.offer(v);}
    }
    return k==org.length;
}
```

## Complexity
Time O(total sequence length), space O(V+E).