# Find Common Characters

## Problem
Return characters that appear in every word, including duplicates.

## Intuition
Keep the minimum frequency of each character across all words. Those minimum counts are exactly the characters common to every word.

## Java
```java
public List<String> commonChars(String[] words) {
    int[] common=new int[26]; Arrays.fill(common,Integer.MAX_VALUE);
    for(String w:words){
        int[] cur=new int[26];
        for(char c:w.toCharArray()) cur[c-'a']++;
        for(int i=0;i<26;i++) common[i]=Math.min(common[i],cur[i]);
    }
    List<String> ans=new ArrayList<>();
    for(int i=0;i<26;i++) while(common[i]-->0) ans.add(String.valueOf((char)('a'+i)));
    return ans;
}
```

## Complexity
Time O(total characters + 26 × number of words), space O(1) excluding output.