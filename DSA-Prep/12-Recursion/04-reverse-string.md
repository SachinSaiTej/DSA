# Reverse String Recursively

## Intuition
Swap the characters at both ends and recurse toward the middle.

## Java
```java
void reverse(char[] s){reverse(s,0,s.length-1);}void reverse(char[]s,int l,int r){if(l>=r)return;char t=s[l];s[l]=s[r];s[r]=t;reverse(s,l+1,r-1);}
```

## Complexity
O(n) time and O(n) recursion stack.