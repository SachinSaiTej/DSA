# Lemonade Change

## Intuition
Maintain counts of $5 and $10 bills. For a $10, give one $5; for a $20, prefer one $10 plus one $5, otherwise three $5s. This preserves smaller bills for future change.

## Java
```java
public boolean lemonadeChange(int[]b){int five=0,ten=0;for(int x:b){if(x==5)five++;else if(x==10){if(five==0)return false;five--;ten++;}else{if(ten>0&&five>0){ten--;five--;}else if(five>=3)five-=3;else return false;}}return true;}
```

## Complexity
O(n) time and O(1) space.