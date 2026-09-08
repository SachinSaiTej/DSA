# Maximum Number of Vowels in a Substring

## Intuition
Keep a fixed-size window of length `k` and maintain the number of vowels inside it.

## Java
```java
public int maxVowels(String s,int k){
    int cur=0,best=0;for(int i=0;i<s.length();i++){if(isVowel(s.charAt(i)))cur++;if(i>=k&&isVowel(s.charAt(i-k)))cur--;if(i>=k-1)best=Math.max(best,cur);}return best;
}
boolean isVowel(char c){return "aeiou".indexOf(c)>=0;}
```

## Complexity
O(n) time, O(1) space.