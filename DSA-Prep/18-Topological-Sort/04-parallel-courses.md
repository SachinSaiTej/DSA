# Parallel Courses

## Problem
Given prerequisite relations, find the minimum number of semesters needed to finish all courses when any number of available courses can be taken together.

## Intuition
Topological BFS by levels: each level is one semester. If not all courses are processed, a cycle exists.

## Java
```java
public int minimumSemesters(int n,int[][]r){
    List<Integer>[]g=new ArrayList[n+1];for(int i=1;i<=n;i++)g[i]=new ArrayList<>();int[]in=new int[n+1];
    for(int[]e:r){g[e[0]].add(e[1]);in[e[1]]++;}Queue<Integer>q=new ArrayDeque<>();for(int i=1;i<=n;i++)if(in[i]==0)q.offer(i);
    int done=0,sem=0;while(!q.isEmpty()){int sz=q.size();sem++;while(sz-->0){int u=q.poll();done++;for(int v:g[u])if(--in[v]==0)q.offer(v);}}return done==n?sem:-1;
}
```

## Complexity
Time O(V+E), space O(V+E).