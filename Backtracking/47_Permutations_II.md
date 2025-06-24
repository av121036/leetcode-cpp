# 47\_Permutations\_II

## 題目描述

給定一個可能包含重複數字的整數陣列 `nums`，請回傳**所有不重複的排列**（permutations）。

你可以按任意順序回傳答案。

---

## 範例

### Example 1:

```
輸入: nums = [1,1,2]
輸出: [
  [1,1,2],
  [1,2,1],
  [2,1,1]
]
```

### Example 2:

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

---

## 解題想法

本題延伸自 46 題，但因輸入可能有重複元素，需要處理 **重複排列的去重問題**。

處理方式：

1. 對 `nums` 排序。
2. 在 backtracking 中跳過「相同值、未被使用的上一個數」：

   ```cpp
   if (i > 0 && nums[i] == nums[i - 1] && !used[i - 1]) continue;
   ```
---

## C++ 程式碼

```cpp
class Solution {
public:
    vector<vector<int>> permuteUnique(vector<int>& nums) {
        vector<vector<int>> res;
        vector<int> path;
        vector<bool> used(nums.size(), false);
        sort(nums.begin(), nums.end());
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
            if (i > 0 && nums[i] == nums[i - 1] && !used[i - 1]) continue;
            path.push_back(nums[i]);
            used[i] = true;
            backtrack(nums, path, used, res);
            used[i] = false;
            path.pop_back();
        }
    }
};
```

---

## 備註
* 排序 + `i > 0 && nums[i] == nums[i - 1] && !used[i - 1]` 是避免重複解的寫法。
