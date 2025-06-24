# 188\_Best\_Time\_to\_Buy\_and\_Sell\_Stock\_IV

## 題目描述

你最多可以完成 **k 次交易**（即最多買入和賣出各 k 次）。

給定整數 `k` 和整數陣列 `prices`，其中第 `i` 天的價格為 `prices[i]`，請找出能獲得的最大利潤。

**注意：你不能同時進行多筆交易（必須先賣出前一張股票才能再次買入）。**

---

## 範例

### Example 1:

```
輸入: k = 2, prices = [2,4,1]
輸出: 2
解釋: 買入1賣出4，利潤 = 3
```

### Example 2:

```
輸入: k = 2, prices = [3,2,6,5,0,3]
輸出: 7
解釋: 買入2賣出6，買入0賣出3，總利潤 = 4 + 3 = 7
```

---

## 解題想法

這題是股票系列的進階版，可視為 **狀態 DP 題目**。

### 特殊情況：

* 若 `k >= prices.size() / 2`，代表不限交易次數，可轉為第 122 題（Greedy 解）。

### 通用情況：使用 DP

定義：

* `dp[i][j]`：最多做 `i` 次交易，在第 `j` 天能得到的最大利潤
* 狀態轉移：

```cpp
dp[i][j] = max(dp[i][j-1], prices[j] + max_diff)
max_diff = max(max_diff, dp[i-1][m] - prices[m])  for m < j
```



---

## C++ 程式碼

```cpp
class Solution {
public:
    int maxProfit(int k, vector<int>& prices) {
        int n = prices.size();
        if (n == 0 || k == 0) return 0;

        // 特判：等於無限次交易
        if (k >= n / 2) {
            int profit = 0;
            for (int i = 1; i < n; ++i) {
                if (prices[i] > prices[i - 1]) {
                    profit += prices[i] - prices[i - 1];
                }
            }
            return profit;
        }

        vector<vector<int>> dp(k + 1, vector<int>(n, 0));
        for (int i = 1; i <= k; ++i) {
            int maxDiff = -prices[0];
            for (int j = 1; j < n; ++j) {
                dp[i][j] = max(dp[i][j - 1], prices[j] + maxDiff);
                maxDiff = max(maxDiff, dp[i - 1][j] - prices[j]);
            }
        }

        return dp[k][n - 1];
    }
};
```