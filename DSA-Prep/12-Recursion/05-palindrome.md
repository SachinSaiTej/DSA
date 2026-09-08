# Palindrome Recursively

## Intuition
Compare the first and last characters. If equal, recursively check the inner substring.

## Java
```java
boolean isPalindrome(String s){return check(s,0,s.length()-1);}boolean check(String s,int l,int r){if(l>=r)return true;return s.charAt(l)==s.charAt(r)&&check(s,l+1,r-1);}
```

## Complexity
O(n) time and O(n) stack.