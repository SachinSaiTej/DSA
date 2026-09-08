# Time Based Key-Value Store

## Intuition
Store each key's values with timestamps in increasing order. For `get`, binary-search the latest timestamp not greater than the requested time.

## Java
```java
class TimeMap{static class E{int t;String v;E(int t,String v){this.t=t;this.v=v;}}Map<String,List<E>>m=new HashMap<>();public void set(String k,String v,int t){m.computeIfAbsent(k,x->new ArrayList<>()).add(new E(t,v));}public String get(String k,int t){List<E>a=m.get(k);if(a==null)return "";int l=0,r=a.size()-1;String ans="";while(l<=r){int x=(l+r)>>>1;if(a.get(x).t<=t){ans=a.get(x).v;l=x+1;}else r=x-1;}return ans;}}
```

## Complexity
`set` O(1) amortized; `get` O(log n); space O(total entries).