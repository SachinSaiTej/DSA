# Coin Change

## Problem
Given coin denominations and an amount, return the minimum number of coins needed to make that amount. Return `-1` if it cannot be formed.

## Intuition
Let `dp[a]` be the minimum coins needed for amount `a`. For every amount, try every coin and build the answer from `a - coin`.

## Java
```java
public int coinChange(int[] coins, int amount) {
    int[] dp = new int[amount + 1];
    Arrays.fill(dp, amount + 1);
    dp[0] = 0;

    for (int a = 1; a <= amount; a++) {
        for (int coin : coins) {
            if (coin <= a) {
                dp[a] = Math.min(dp[a], dp[a - coin] + 1);
            }
        }
    }
    return dp[amount] > amount ? -1 : dp[amount];
}
```

## Complexity
Time O(amount × number of coins), space O(amount).