# Find All Anagrams in a String

## Intuition
Every anagram has identical character counts. Slide a window of length `p.length()` and compare its counts with the pattern.

## Java
```java
public List<Integer> findAnagrams(String s,String p){
    List<Integer> ans=new ArrayList<>();if(p.length()>s.length())return ans;int[] a=new int[26],b=new int[26];
    for(char c:p.toCharArray())a[c-'a']++;
    for(int i=0;i<s.length();i++){b[s.charAt(i)-'a']++;if(i>=p.length())b[s.charAt(i-p.length())-'a']--;if(i>=p.length()-1&&Arrays.equals(a,b))ans.add(i-p.length()+1);}
    return ans;
}
```

## Complexity
O(26n) time, O(1) space.