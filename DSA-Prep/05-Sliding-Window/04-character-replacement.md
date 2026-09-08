# Longest Repeating Character Replacement

## Intuition
Maintain character frequencies in the window. The window is valid when `windowSize - maxFrequency <= k`; otherwise shrink it.

## Java
```java
public int characterReplacement(String s,int k){
    int[] f=new int[26];int l=0,max=0,best=0;
    for(int r=0;r<s.length();r++){max=Math.max(max,++f[s.charAt(r)-'A']);while(r-l+1-max>k)f[s.charAt(l++)-'A']--;best=Math.max(best,r-l+1);}
    return best;
}
```

## Complexity
O(n) time, O(1) space.