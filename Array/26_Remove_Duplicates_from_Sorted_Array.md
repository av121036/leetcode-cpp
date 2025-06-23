# 26. Remove Duplicates from Sorted Array

## 題目描述

給定一個**已排序**的整數陣列 `nums`，請**就地刪除重複項**，使每個元素只出現一次，並回傳新長度。

不要使用額外的陣列空間，必須使用 O(1) 額外記憶體，就地修改輸入陣列。

---

## 範例

### Example 1:

```
輸入: nums = [1,1,2]
輸出: 2, nums = [1,2,_]
```

### Example 2:

```
輸入: nums = [0,0,1,1,1,2,2,3,3,4]
輸出: 5, nums = [0,1,2,3,4,_...]
```

---

## 解題想法

* 使用「快慢指標」：

  * `slow`：標記目前結果的末端位置
  * `fast`：遍歷整個陣列，遇到不重複的值就寫入到 `slow + 1` 位置
* 當兩值不相等時，將 `nums[fast]` 覆蓋寫入 `nums[++slow]`

時間複雜度：`O(n)`
空間複雜度：`O(1)`

---

## C++ 程式碼

```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if (nums.empty()) return 0;
        int slow = 0;
        for (int fast = 1; fast < nums.size(); ++fast) {
            if (nums[fast] != nums[slow]) {
                ++slow;
                nums[slow] = nums[fast];
            }
        }
        return slow + 1;
    }
};
```
