# Accounts Merge

## Problem
Merge accounts belonging to the same person when they share an email address.

## Intuition
Treat emails as nodes. Union emails appearing in the same account, then group emails by their DSU root.

## Java
```java
public List<List<String>> accountsMerge(List<List<String>>a){
    Map<String,Integer>id=new HashMap<>();List<String>emails=new ArrayList<>();int n=0;
    for(List<String>x:a)for(int i=1;i<x.size();i++)if(!id.containsKey(x.get(i))){id.put(x.get(i),n++);emails.add(x.get(i));}
    DSU d=new DSU(n);for(List<String>x:a)for(int i=2;i<x.size();i++)d.union(id.get(x.get(1)),id.get(x.get(i)));
    Map<Integer,List<String>>g=new HashMap<>();for(String e:id.keySet())g.computeIfAbsent(d.find(id.get(e)),z->new ArrayList<>()).add(e);
    List<List<String>>ans=new ArrayList<>();for(List<String>x:g.values()){Collections.sort(x);List<String>r=new ArrayList<>();r.add(a.get(findOwner(a,x,id)).get(0));r.addAll(x);ans.add(r);}return ans;
}
int findOwner(List<List<String>>a,List<String>x,Map<String,Integer>id){for(int i=0;i<a.size();i++)if(a.get(i).size()>1&&id.containsKey(a.get(i).get(1))&&x.contains(a.get(i).get(1)))return i;return 0;}
static class DSU{int[]p;DSU(int n){p=new int[n];for(int i=0;i<n;i++)p[i]=i;}int find(int x){return p[x]==x?x:(p[x]=find(p[x]));}void union(int a,int b){a=find(a);b=find(b);if(a!=b)p[b]=a;}}
```

## Complexity
Time O(E α(V) + S log S), space O(V+E).