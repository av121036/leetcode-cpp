# 122\_Best\_Time\_to\_Buy\_and\_Sell\_Stock\_II

## 題目描述

給定一個整數陣列 `prices`，其中第 `i` 天的價格為 `prices[i]`，你可以不限次數地買進和賣出股票（**同一天可以先買後賣**）。

設計一個演算法來計算你能獲得的最大利潤。

**你不能同時持有多張股票（必須先賣掉前一張，才能再次買進）。**

---

## 範例

### Example 1:

```
輸入: prices = [7,1,5,3,6,4]
輸出: 7
解釋: 買入1->賣出5，買入3->賣出6，共利潤 4+3=7
```

### Example 2:

```
輸入: prices = [1,2,3,4,5]
輸出: 4
解釋: 每天買入賣出都可以，總利潤為 4
```

### Example 3:

```
輸入: prices = [7,6,4,3,1]
輸出: 0
解釋: 永遠沒有利潤可圖。
```

---

## 解題想法

這是一題 **貪心（Greedy）** 題：

* 只要今天價格比昨天高，就假設昨天買今天賣，把所有這種上漲利潤累加即可。

**不需要真的模擬買進/賣出，只需要累加「所有正利潤段」即可。**

---

## C++ 程式碼

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int profit = 0;
        for (int i = 1; i < prices.size(); ++i) {
            if (prices[i] > prices[i - 1]) {
                profit += prices[i] - prices[i - 1];
            }
        }
        return profit;
    }
};
```
