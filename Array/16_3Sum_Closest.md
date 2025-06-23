# 16. 3Sum Closest

## 題目描述

給定一個整數陣列 `nums` 和一個目標值 `target`，找出陣列中**和最接近目標值**的三個整數，使它們的總和最接近 `target`。

回傳這三個數字的總和。

假設只有一組答案。

---

## 範例

### Example 1:

```
輸入: nums = [-1,2,1,-4], target = 1
輸出: 2
解釋: 最接近的三數和為 2 (-1 + 2 + 1 = 2)
```

### Example 2:

```
輸入: nums = [0,0,0], target = 1
輸出: 0
```

---

## 解題想法

1. 對陣列 `nums` 進行排序。
2. 固定一個索引 `i`，其餘使用雙指標 `left` 與 `right` 掃描。
3. 每次計算三數總和，並與目標值 `target` 比較距離。
4. 更新目前最接近的結果 `closestSum`。
5. 若總和小於 target，左指標右移；若總和大於 target，右指標左移。
---

## C++ 程式碼

```cpp
class Solution {
public:
    int threeSumClosest(vector<int>& nums, int target) {
        sort(nums.begin(), nums.end());
        int n = nums.size();
        int closest = nums[0] + nums[1] + nums[2];
        for (int i = 0; i < n - 2; ++i) {
            int left = i + 1, right = n - 1;
            while (left < right) {
                int sum = nums[i] + nums[left] + nums[right];
                if (abs(sum - target) < abs(closest - target)) {
                    closest = sum;
                }
                if (sum < target) {
                    ++left;
                } else if (sum > target) {
                    --right;
                } else {
                    return target; // 完全相等的情況，直接回傳
                }
            }
        }
        return closest;
    }
};
```

---

## 備註

* 與 3Sum 題類似，但本題不需去重與收集所有組合，只需維護一個最佳解。
* 差值比較使用 `abs()` 計算距離。
* 若答案可能不唯一，但題目保證有唯一最接近解，因此一旦遇到完全等於 `target` 可提早回傳。
