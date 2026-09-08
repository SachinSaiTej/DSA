# Coin Change

## Problem
Given coin denominations and an amount, find the minimum number of coins needed to make that amount.

## Intuition
Let `dp[a]` be the minimum coins for amount `a`. For every coin, try taking it and build from the smaller amount.

## Java
```java
public int coinChange(int[] coins, int amount) {
    int[] dp=new int[amount+1];
    Arrays.fill(dp, amount+1); dp[0]=0;
    for(int a=1;a<=amount;a++)
        for(int c:coins) if(c<=a) dp[a]=Math.min(dp[a],dp[a-c]+1);
    return dp[amount]>amount?-1:dp[amount];
}
```

## Complexity
Time O(amount × number of coins), space O(amount).