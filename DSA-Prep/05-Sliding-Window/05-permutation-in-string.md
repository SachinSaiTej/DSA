# Permutation in String

## Intuition
A permutation has the same character counts as the pattern. Maintain a fixed-size window and compare frequency arrays.

## Java
```java
public boolean checkInclusion(String s1,String s2){
    if(s1.length()>s2.length())return false;int[] a=new int[26],b=new int[26];
    for(char c:s1.toCharArray())a[c-'a']++;
    for(int i=0;i<s2.length();i++){b[s2.charAt(i)-'a']++;if(i>=s1.length())b[s2.charAt(i-s1.length())-'a']--;if(Arrays.equals(a,b))return true;}
    return false;
}
```

## Complexity
O(26n) time, O(1) space.