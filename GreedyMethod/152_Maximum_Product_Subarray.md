# 152\_Maximum\_Product\_Subarray

## 題目描述

給定一個整數陣列 `nums`，找出一個連續子陣列，使其「乘積」最大，並回傳該乘積。

子陣列至少包含一個元素。

---

## 範例

### Example 1:

```
輸入: nums = [2,3,-2,4]
輸出: 6
解釋: 子陣列 [2,3] 有最大乘積 6
```

### Example 2:

```
輸入: nums = [-2,0,-1]
輸出: 0
解釋: 子陣列 [-2,0] 或 [0,-1] 的最大乘積為 0
```

---

## 解題思路

這題與 53 題最大子陣列總和類似，但更複雜：因為**負數相乘會變正數**，所以需要追蹤：

* `maxProd`: 到目前為止的最大乘積
* `minProd`: 到目前為止的最小乘積（可能被下一個負數翻轉成最大）

動態規劃轉移：

```cpp
maxProd = max({nums[i], nums[i] * maxProd, nums[i] * minProd});
minProd = min({nums[i], nums[i] * maxPrev, nums[i] * minProd});
```

記得先暫存前一步最大值 `maxPrev`，避免被覆蓋。

---

## C++ 程式碼

```cpp
class Solution {
public:
    int maxProduct(vector<int>& nums) {
        int maxProd = nums[0];
        int minProd = nums[0];
        int res = nums[0];

        for (int i = 1; i < nums.size(); ++i) {
            int prevMax = maxProd;
            maxProd = max({nums[i], nums[i] * maxProd, nums[i] * minProd});
            minProd = min({nums[i], nums[i] * prevMax, nums[i] * minProd});
            res = max(res, maxProd);
        }

        return res;
    }
};
```

---

## 備註

* 與最大總和題 53 題對比：多了負數/0 的處理。

