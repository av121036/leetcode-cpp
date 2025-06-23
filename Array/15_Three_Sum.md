# 15. Three Sum

## 題目描述

給定一個整數陣列 `nums`，請你找出所有不重複的三元組 `[nums[i], nums[j], nums[k]]`，使得它們的總和為 0。

你不能使用相同的元素索引兩次。

---

## 範例

### Example 1:

```
輸入: nums = [-1,0,1,2,-1,-4]
輸出: [[-1,-1,2],[-1,0,1]]
```

### Example 2:

```
輸入: nums = []
輸出: []
```

### Example 3:

```
輸入: nums = [0]
輸出: []
```

---

## 解題想法

1. 對陣列先進行排序。
2. 固定一個元素 nums\[i]，再使用左右雙指標（two pointer）尋找 `nums[j] + nums[k] = -nums[i]`。
3. 若總和為 0，加入答案並跳過重複元素。
4. 若總和小於 0，左指標右移；大於 0，右指標左移。
5. 注意跳過重複值避免重複組合。

---

## C++ 程式碼

```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        vector<vector<int>> ans;
        int n = nums.size();
        for (int i = 0; i < n; ++i) {
            if (i > 0 && nums[i] == nums[i - 1]) continue; // 避免重複
            int left = i + 1, right = n - 1;
            while (left < right) {
                int sum = nums[i] + nums[left] + nums[right];
                if (sum == 0) {
                    ans.push_back({nums[i], nums[left], nums[right]});
                    while (left < right && nums[left] == nums[left + 1]) ++left;
                    while (left < right && nums[right] == nums[right - 1]) --right;
                    ++left;
                    --right;
                } else if (sum < 0) {
                    ++left;
                } else {
                    --right;
                }
            }
        }
        return ans;
    }
};
```

