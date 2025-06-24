# 46\_Permutations

## 題目描述

給定一個不含重複數字的整數陣列 `nums`，請回傳所有可能的排列（permutations）。

你可以按任意順序回傳答案。

---

## 範例

### Example 1:

```
輸入: nums = [1,2,3]
輸出: [
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```

### Example 2:

```
輸入: nums = [0,1]
輸出: [[0,1],[1,0]]
```

### Example 3:

```
輸入: nums = [1]
輸出: [[1]]
```

---

## 解題想法

這題屬於經典的 **Backtracking（回溯法）** 題型：

1. 每一層遞迴代表選擇一個數字。
2. 若當前數字未被使用（可用 `used` 陣列紀錄），就選擇它並繼續遞迴。
3. 當選滿 `nums.size()` 個元素時，記錄下來。

---

## C++ 程式碼

```cpp
class Solution {
public:
    vector<vector<int>> permute(vector<int>& nums) {
        vector<vector<int>> res;
        vector<int> path;
        vector<bool> used(nums.size(), false);
        backtrack(nums, path, used, res);
        return res;
    }

private:
    void backtrack(vector<int>& nums, vector<int>& path,
                   vector<bool>& used, vector<vector<int>>& res) {
        if (path.size() == nums.size()) {
            res.push_back(path);
            return;
        }
        for (int i = 0; i < nums.size(); ++i) {
            if (used[i]) continue;
            path.push_back(nums[i]);
            used[i] = true;
            backtrack(nums, path, used, res);
            used[i] = false;
            path.pop_back();
        }
    }
};
```