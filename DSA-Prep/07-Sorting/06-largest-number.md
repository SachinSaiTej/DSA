# Largest Number

## Intuition
Sort numbers using concatenation: `a` should come before `b` when `ab > ba`. Join the result and handle leading zeroes.

## Java
```java
public String largestNumber(int[]a){String[]s=new String[a.length];for(int i=0;i<a.length;i++)s[i]=String.valueOf(a[i]);Arrays.sort(s,(x,y)->(y+x).compareTo(x+y));if(s[0].equals("0"))return "0";return String.join("",s);}
```

## Complexity
O(n log n) comparisons, O(n) space.