## 题目描述

You are given an array `prices` where `prices[i]` is the price of a given stock on the `ith` day.

You want to maximize your profit by choosing a **single day** to buy one stock and choosing a **different day in the future** to sell that stock.

Return *the maximum profit you can achieve from this transaction*. If you cannot achieve any profit, return `0`.

 

**Example 1:**

```
Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.
```

**Example 2:**

```
Input: prices = [7,6,4,3,1]
Output: 0
Explanation: In this case, no transactions are done and the max profit = 0.
```

 

**Constraints:**

- `1 <= prices.length <= 105`
- `0 <= prices[i] <= 104`

------

> ### 两种解法
>
> 1. 暴力解法
> 2. One Pass 解法
>    - 变量一：max profit = -∞
>    - 变量二：min price = ∞

## One Pass 解法

#### Pyhton3

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        max_profit = float('-inf')
        min_price = float('inf')

        for price in prices:
            min_price = min(min_price, price)
            max_profit = max(max_profit, price - min_price)
        return max_profit
```

执行用时：328 ms

内存消耗：23.4 MB

## 