# 27. Remove Element

## 題目描述

給定一個陣列 `nums` 和一個值 `val`，請你就地移除所有數值等於 `val` 的元素，並回傳移除後陣列的新長度。

元素的順序可以改變。你不需要考慮超出新長度後面的元素。

---

## 範例

### Example 1:

```
輸入: nums = [3,2,2,3], val = 3
輸出: 2, nums = [2,2,_]
```

### Example 2:

```
輸入: nums = [0,1,2,2,3,0,4,2], val = 2
輸出: 5, nums = [0,1,4,0,3,_...]
```

---

## 解題想法

* 使用 `slow` 指標：紀錄下一個應該保留的位置。
* `fast` 指標遍歷整個陣列。
* 當 `nums[fast] != val` 時，把它寫到 `nums[slow]` 並 `slow++`。

---

## C++ 程式碼

```cpp
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int slow = 0;
        for (int fast = 0; fast < nums.size(); ++fast) {
            if (nums[fast] != val) {
                nums[slow++] = nums[fast];
            }
        }
        return slow;
    }
};
```
