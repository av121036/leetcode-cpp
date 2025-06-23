# 217. Contains Duplicate

## 題目描述

給定一個整數陣列 `nums`，請判斷陣列中是否存在重複元素。

如果任意一個值在陣列中出現至少兩次，回傳 `true`。如果每個元素都不相同，回傳 `false`。

---

## 範例

### Example 1:

```
輸入: nums = [1,2,3,1]
輸出: true
```

### Example 2:

```
輸入: nums = [1,2,3,4]
輸出: false
```

### Example 3:

```
輸入: nums = [1,1,1,3,3,4,3,2,4,2]
輸出: true
```

---

## 解題想法

此題可以使用 Hash Set 來追蹤是否有重複元素出現：

* 建立一個 `unordered_set` 來儲存出現過的數字。
* 遍歷陣列，若當前數字已經出現在 set 中，表示出現重複，回傳 `true`。
* 若遍歷結束皆無重複，回傳 `false`。

---

## C++ 程式碼

```cpp
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        unordered_set<int> seen;
        for (int num : nums) {
            if (seen.count(num)) return true;
            seen.insert(num);
        }
        return false;
    }
};
```
