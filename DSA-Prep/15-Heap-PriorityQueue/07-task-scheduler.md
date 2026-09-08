# Task Scheduler

## Problem
Schedule tasks with cooldown `n` between identical tasks using the minimum number of intervals.

## Intuition
The most frequent task determines the required frame. Fill idle slots around the most frequent tasks, then use remaining tasks to fill them.

## Java
```java
public int leastInterval(char[]tasks,int n){int[]f=new int[26];for(char c:tasks)f[c-'A']++;Arrays.sort(f);int max=f[25],slots=(max-1)*n;for(int i=24;i>=0;i--)slots-=Math.min(max-1,f[i]);return tasks.length+Math.max(0,slots);}
```

## Complexity
O(T + 26 log 26), effectively O(T) time and O(1) extra space.