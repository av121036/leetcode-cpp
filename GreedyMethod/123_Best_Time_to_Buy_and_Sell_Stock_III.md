# 123\_Best\_Time\_to\_Buy\_and\_Sell\_Stock\_III

## 題目描述

你最多可以完成 **兩次** 交易（即最多買入和賣出各兩次），但必須先賣出股票才能再次買入。

給定整數陣列 `prices`，其中第 `i` 天的價格為 `prices[i]`，請找出能獲得的最大利潤。

---

## 範例

### Example 1:

```
輸入: prices = [3,3,5,0,0,3,1,4]
輸出: 6
解釋: 買入0賣出3，再買入1賣出4，總利潤 = 6
```

### Example 2:

```
輸入: prices = [1,2,3,4,5]
輸出: 4
```

### Example 3:

```
輸入: prices = [7,6,4,3,1]
輸出: 0
```

---

## 解題想法

這題可以用 **動態規劃（Dynamic Programming）** 或 **貪心法 + 狀態變數法** 來解。

我們定義四個狀態變數：

* `buy1`: 第一次買入的最大收益（取負數）
* `sell1`: 第一次賣出的最大利潤
* `buy2`: 第二次買入的最大收益（扣掉 sell1）
* `sell2`: 第二次賣出的最大利潤（最終答案）

每一步更新：

```cpp
buy1  = max(buy1, -price);
sell1 = max(sell1, buy1 + price);
buy2  = max(buy2, sell1 - price);
sell2 = max(sell2, buy2 + price);
```
---

## C++ 程式碼

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int buy1 = INT_MIN, sell1 = 0;
        int buy2 = INT_MIN, sell2 = 0;

        for (int price : prices) {
            buy1 = max(buy1, -price);
            sell1 = max(sell1, buy1 + price);
            buy2 = max(buy2, sell1 - price);
            sell2 = max(sell2, buy2 + price);
        }

        return sell2;
    }
};
```

