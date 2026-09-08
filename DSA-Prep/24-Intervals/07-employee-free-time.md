# Employee Free Time

## Problem
Given each employee's non-overlapping busy intervals, return the common free intervals.

## Intuition
Flatten all intervals and sort by start. Track the latest end seen. A gap before the next start is common free time.

## Java
```java
public List<Interval> employeeFreeTime(List<List<Interval>> schedule){
    List<Interval> all=new ArrayList<>();for(List<Interval>s:schedule)all.addAll(s);
    all.sort((a,b)->Integer.compare(a.start,b.start));List<Interval>ans=new ArrayList<>();int end=all.get(0).end;
    for(int i=1;i<all.size();i++){Interval x=all.get(i);if(x.start>end)ans.add(new Interval(end,x.start));end=Math.max(end,x.end);}return ans;
}
```

## Complexity
Time O(N log N), space O(N).