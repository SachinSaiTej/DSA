# Asteroid Collision

## Intuition
Use a stack. A collision occurs only when the stack top moves right and the current asteroid moves left. Keep resolving collisions until one survives or both destroy each other.

## Java
```java
public int[] asteroidCollision(int[]a){Deque<Integer>s=new ArrayDeque<>();for(int x:a){boolean alive=true;while(alive&&x<0&&!s.isEmpty()&&s.peek()>0){if(s.peek()<-x)s.pop();else if(s.peek()==-x){s.pop();alive=false;}else alive=false;}if(alive)s.push(x);}int[]o=new int[s.size()];for(int i=o.length-1;i>=0;i--)o[i]=s.pop();return o;}
```

## Complexity
O(n) time, O(n) space.