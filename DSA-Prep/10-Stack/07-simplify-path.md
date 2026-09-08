# Simplify Path

## Intuition
Treat `/` as separators, ignore empty parts and `.`, and use a stack for directory names. `..` removes the latest directory when possible.

## Java
```java
public String simplifyPath(String path){Deque<String>s=new ArrayDeque<>();for(String p:path.split("/")){if(p.isEmpty()||p.equals("."))continue;if(p.equals("..")){if(!s.isEmpty())s.pop();}else s.push(p);}StringBuilder b=new StringBuilder();while(!s.isEmpty())b.append('/').append(s.removeLast());return b.length()==0?"/":b.toString();}
```

## Complexity
O(n) time, O(n) space.