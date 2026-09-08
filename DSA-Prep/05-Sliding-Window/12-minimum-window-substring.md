# Minimum Window Substring

## Intuition
Maintain counts required from `t`. Expand right until all requirements are met, then shrink left while still valid to find the smallest window.

## Java
```java
public String minWindow(String s,String t){
    if(t.length()>s.length())return "";int[] need=new int[128];for(char c:t.toCharArray())need[c]++;int missing=t.length(),l=0,start=0,len=Integer.MAX_VALUE;
    for(int r=0;r<s.length();r++){if(need[s.charAt(r)]>0)missing--;need[s.charAt(r)]--;while(missing==0){if(r-l+1<len){len=r-l+1;start=l;}need[s.charAt(l)]++;if(need[s.charAt(l)]>0)missing++;l++;}}
    return len==Integer.MAX_VALUE?"":s.substring(start,start+len);
}
```

## Complexity
O(n) time, O(1) space for ASCII.