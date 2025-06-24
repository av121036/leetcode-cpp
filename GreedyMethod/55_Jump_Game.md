# 55\_Jump\_Game

## 題目描述

給定一個非負整數陣列 `nums`，其中 `nums[i]` 表示從索引 `i` 最多可以跳躍的步數，請判斷是否能「從索引 0 跳到最後一個索引」。

---

## 範例

### Example 1:

```
輸入: nums = [2,3,1,1,4]
輸出: true
解釋: 可以跳到最後一個位置，如 0 -> 1 -> 4。
```

### Example 2:

```
輸入: nums = [3,2,1,0,4]
輸出: false
解釋: 無法跳到最後一個位置。
```

---

## 解題想法

* 維護一個變數 `farthest` 代表目前能跳到的最遠位置。
* 遍歷過程中若 `i > farthest` 表示此位置根本無法抵達，直接回傳 `false`。
* 若最遠位置能到或超過最後一格，回傳 `true`。

---

## C++ 程式碼

```cpp
class Solution {
public:
    bool canJump(vector<int>& nums) {
        int farthest = 0;
        for (int i = 0; i < nums.size(); ++i) {
            if (i > farthest) return false;
            farthest = max(farthest, i + nums[i]);
        }
        return true;
    }
};
```
