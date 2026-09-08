# Backspace String Compare

## Problem
Compare two strings after interpreting `#` as a backspace.

## Intuition
Scan from right to left while counting pending backspaces. This avoids building the processed strings.

## Java
```java
public boolean backspaceCompare(String s,String t){
    int i=s.length()-1,j=t.length()-1,skipS=0,skipT=0;
    while(i>=0||j>=0){
        while(i>=0){if(s.charAt(i)=='#'){skipS++;i--;}else if(skipS>0){skipS--;i--;}else break;}
        while(j>=0){if(t.charAt(j)=='#'){skipT++;j--;}else if(skipT>0){skipT--;j--;}else break;}
        if(i<0||j<0)return i<0&&j<0;
        if(s.charAt(i--)!=t.charAt(j--))return false;
    }
    return true;
}
```

## Complexity
Time O(n+m), space O(1).