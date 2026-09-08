# Best Time to Buy and Sell Stock

## Problem
Given daily stock prices, choose one day to buy and a later day to sell to maximize profit.

## Intuition
While scanning left to right, keep the cheapest price seen so far. Selling today gives `price - minPrice`; keep the maximum profit.

## Java
```java
public int maxProfit(int[] prices) {
    int minPrice = Integer.MAX_VALUE;
    int maxProfit = 0;

    for (int price : prices) {
        minPrice = Math.min(minPrice, price);
        maxProfit = Math.max(maxProfit, price - minPrice);
    }
    return maxProfit;
}
```

## Complexity
Time O(n), space O(1).

## Interview Point
You do not need to remember the actual buy/sell days unless the problem asks for them; the minimum price and maximum profit are sufficient.