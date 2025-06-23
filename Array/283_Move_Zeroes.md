# 283. Move Zeroes

## 題目描述

給定一個整數陣列 `nums`，將所有的 `0` 移動到陣列的末尾，同時保持非零元素的相對順序。

你必須就地（in-place）完成此操作，而不複製額外的陣列。

---

## 範例

### Example 1:

```
輸入: nums = [0,1,0,3,12]
輸出: [1,3,12,0,0]
```

### Example 2:

```
輸入: nums = [0]
輸出: [0]
```

---

## 解題想法

* 使用雙指標：

  * `slow` 指向下一個非零元素應該放的位置。
  * `fast` 遍歷整個陣列，若遇到非零元素就與 `slow` 位置交換，然後 `slow++`。

---

## C++ 程式碼

```cpp
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int slow = 0;
        for (int fast = 0; fast < nums.size(); ++fast) {
            if (nums[fast] != 0) {
                swap(nums[slow++], nums[fast]);
            }
        }
    }
};
```
