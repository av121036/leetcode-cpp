# 1. Two Sum

## 題目描述

給定一個整數陣列 `nums` 和一個目標值 `target`，請你在該陣列中找出**兩個**數字，使它們的和為目標值，並回傳它們的**索引**。

你可以假設每個輸入只對應一個答案。但你不能重複使用同一個元素。

你可以以任意順序回傳答案。

---

## 範例

### Example 1:

```
輸入: nums = [2,7,11,15], target = 9
輸出: [0,1]
解釋: 因為 nums[0] + nums[1] == 9，回傳 [0, 1]。
```

### Example 2:

```
輸入: nums = [3,2,4], target = 6
輸出: [1,2]
```

### Example 3:

```
輸入: nums = [3,3], target = 6
輸出: [0,1]
```

---

## 解題思路

使用 Hash Table 儲存已遍歷過的數字與其索引。

每次遍歷時，計算 `target - nums[i]` 是否已存在於 Hash Table 中：

* 若存在：說明找到了兩個數字相加為 target，回傳它們的索引。
* 若不存在：將 `nums[i]` 與對應索引加入 Hash Table。

---

## C++ 程式碼

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        map<int, int> hash;
        for (int i = 0; i < nums.size(); ++i) {
            int diff = target - nums[i];
            if (hash.count(diff)) {
                return {hash[diff], i};
            }
            hash[nums[i]] = i;
        }
        return {};
    }
};