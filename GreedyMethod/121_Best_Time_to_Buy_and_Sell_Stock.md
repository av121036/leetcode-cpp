# 121\_Best\_Time\_to\_Buy\_and\_Sell\_Stock

## 題目描述

給定一個整數陣列 `prices`，其中第 `i` 天的價格為 `prices[i]`。

你只能**進行一次交易（買入並賣出一次）**，請找出能獲得的最大利潤。

若無法獲得任何利潤，回傳 0。

---

## 範例

### Example 1:

```
輸入: prices = [7,1,5,3,6,4]
輸出: 5
解釋: 在第 2 天買入 (價格 = 1)，第 5 天賣出 (價格 = 6)，利潤 = 6-1 = 5
```

### Example 2:

```
輸入: prices = [7,6,4,3,1]
輸出: 0
解釋: 沒有交易是有利可圖的。
```

---

## 解題想法

這題可用 **一次遍歷（O(n)）+ 貪心策略** 解：

* 在遍歷過程中，記錄歷史最低價 `minPrice`
* 每天都嘗試「當天價格 - 歷史最低價」是否為最大利潤

---

## C++ 程式碼

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int minPrice = INT_MAX;
        int maxProfit = 0;
        for (int price : prices) {
            minPrice = min(minPrice, price);
            maxProfit = max(maxProfit, price - minPrice);
        }
        return maxProfit;
    }
};
```

---

## 備註

* 此題為 122 的簡化版，只能交易一次。

