# Partition Labels

## Intuition
Record the last occurrence of every character. While scanning a segment, extend its end to the furthest last occurrence of any character inside it. When the scan reaches that end, the segment can be closed.

## Java
```java
public List<Integer> partitionLabels(String s){int[]last=new int[26];for(int i=0;i<s.length();i++)last[s.charAt(i)-'a']=i;List<Integer>a=new ArrayList<>();int end=0,start=0;for(int i=0;i<s.length();i++){end=Math.max(end,last[s.charAt(i)-'a']);if(i==end){a.add(i-start+1);start=i+1;}}return a;}
```

## Complexity
O(n) time and O(1) space.