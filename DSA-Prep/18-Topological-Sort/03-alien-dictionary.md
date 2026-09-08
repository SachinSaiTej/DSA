# Alien Dictionary

## Problem
Given words sorted according to an unknown alphabet, derive a valid ordering of the characters.

## Intuition
Compare adjacent words. The first differing characters establish a directed ordering. Topologically sort those character constraints. A prefix violation means invalid input.

## Java
```java
public String alienOrder(String[] w){
    Map<Character,Set<Character>>g=new HashMap<>();Map<Character,Integer>in=new HashMap<>();
    for(String s:w)for(char c:s.toCharArray()){g.putIfAbsent(c,new HashSet<>());in.putIfAbsent(c,0);}
    for(int i=0;i<w.length-1;i++){String a=w[i],b=w[i+1];int n=Math.min(a.length(),b.length()),j=0;while(j<n&&a.charAt(j)==b.charAt(j))j++;if(j==n&&a.length()>b.length())return "";if(j<n&&g.get(a.charAt(j)).add(b.charAt(j)))in.put(b.charAt(j),in.get(b.charAt(j))+1);}
    Queue<Character>q=new ArrayDeque<>();for(char c:in.keySet())if(in.get(c)==0)q.offer(c);StringBuilder ans=new StringBuilder();while(!q.isEmpty()){char c=q.poll();ans.append(c);for(char v:g.get(c))if(--in.put(v,in.get(v)-1)==0)q.offer(v);}
    return ans.length()==in.size()?ans.toString():"";
}
```

## Complexity
Time O(total input characters), space O(V+E).