# 力扣题库 - 买卖股票的最佳时机
## 想法
## Python
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        if not prices:
            return 0
        min_price = float('inf')
        max_profit = 0
        for price in prices:
            if price < min_price:
                min_price = price
            elif price - min_price > max_profit:
                max_profit = price - min_price
        return max_profit    
```
### 复杂度
- 时间复杂度：O(N),执行时间：19ms
- 空间复杂度：O(1),消耗内存：26.40MB
## C
```c
int maxProfit(int* prices, int pricesSize) {
    if (prices == NULL) {
        return 0;
    }
    int min_price = prices[0];
    int profit = 0;
    for (int i = 0; i < pricesSize; i++) {
        if (prices[i] < min_price) {
            min_price = prices[i];
        } else if (prices[i] - min_price > profit) {
            profit = prices[i] - min_price;
        }
    }
    return profit;
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：0ms
- 空间复杂度：O(1),消耗内存：14.93MB
## Java
```java
class Solution {
    public int maxProfit(int[] prices) {
        if ( prices == null ) {
            return 0;
        }
        int min_price = prices[0];
        int profit = 0;
        for (int i = 0; i < prices.length; i++) {
            if (prices[i] < min_price) {
                min_price = prices[i];
            } else if (prices[i] - min_price > profit) {
                profit = prices[i] - min_price;
            }
        }
        return profit;
    }
}
```
### 复杂度
- 时间复杂度：O(N),执行时间：1ms
- 空间复杂度：O(1),消耗内存：92.32MB