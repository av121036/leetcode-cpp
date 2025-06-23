# 80. Remove Duplicates from Sorted Array II

## 題目描述

給定一個**已排序**的整數陣列 `nums`，請就地刪除重複項，使得每個元素**最多出現兩次**，並回傳新的長度。

不要使用額外的陣列空間，必須使用 O(1) 額外記憶體，就地修改輸入陣列。

---

## 範例

### Example 1:

```
輸入: nums = [1,1,1,2,2,3]
輸出: 5, nums = [1,1,2,2,3,_]
```

### Example 2:

```
輸入: nums = [0,0,1,1,1,1,2,3,3]
輸出: 7, nums = [0,0,1,1,2,3,3,_...]
```

---

## 解題想法

* 本題是 26 題的延伸：這次允許**每個數最多出現兩次**。
* 使用 `slow` 指標指向下一個要寫入的位置。
* 條件改為：若 `nums[fast] != nums[slow - 2]`，表示前兩個值中至少有一個不同，才保留。

---

## C++ 程式碼

```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int n = nums.size();
        if (n <= 2) return n;
        int slow = 2;
        for (int fast = 2; fast < n; ++fast) {
            if (nums[fast] != nums[slow - 2]) {
                nums[slow++] = nums[fast];
            }
        }
        return slow;
    }
};
```

---

## 備註

* 關鍵條件：`nums[fast] != nums[slow - 2]`
* 本題可以擴展為允許重複 k 次的版本：只需改成 `slow - k` 判斷即可。
* 若輸入長度小於等於 2，直接回傳即可。
