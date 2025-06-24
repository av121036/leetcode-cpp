# 45\_Jump\_Game\_II

## 題目描述

給定一個非負整數陣列 `nums`，其中 `nums[i]` 代表你從索引 `i` 最多可以跳躍的距離。

請你計算從索引 0 跳到最後一個索引所需的**最少跳躍次數**。

假設你總是可以到達最後一個索引。

---

## 範例

### Example 1:

```
輸入: nums = [2,3,1,1,4]
輸出: 2
解釋: 路徑為 0 -> 1 -> 4
```

### Example 2:

```
輸入: nums = [2,3,0,1,4]
輸出: 2
```

---

## 解題想法


我們希望用「最少的跳躍次數」抵達終點，因此每次都儘可能跳到「當前可達的最遠位置」。

1. 使用 `end` 代表當前這一步可以跳到的最遠邊界。
2. 使用 `farthest` 記錄從目前這一步能跳到的最大距離。
3. 當走到 `i == end` 時，代表需要跳下一步，`step++`，並更新 `end = farthest`。

---

## C++ 程式碼

```cpp
class Solution {
public:
    int jump(vector<int>& nums) {
        int end = 0, farthest = 0, steps = 0;
        for (int i = 0; i < nums.size() - 1; ++i) {
            farthest = max(farthest, i + nums[i]);
            if (i == end) {
                ++steps;
                end = farthest;
            }
        }
        return steps;
    }
};
```