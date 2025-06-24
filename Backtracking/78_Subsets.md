# 78\_Subsets

## 題目描述

給定一個**不包含重複元素**的整數陣列 `nums`，請你回傳該陣列的所有子集（**幂集**）。

你可以按任意順序回傳答案。

---

## 範例

### Example 1:

```
輸入: nums = [1,2,3]
輸出: [
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]
```

### Example 2:

```
輸入: nums = [0]
輸出: [[0],[]]
```

---

## 解題想法

1. 每一層遞迴代表選或不選一個數字。
2. 每次都可以把目前的 path（子集）加進結果。
3. 因為沒有重複元素，所以不需要跳過重複。

---

## C++ 程式碼

```cpp
class Solution {
public:
    vector<vector<int>> subsets(vector<int>& nums) {
        vector<vector<int>> res;
        vector<int> path;
        backtrack(nums, 0, path, res);
        return res;
    }

private:
    void backtrack(vector<int>& nums, int start, vector<int>& path,
                   vector<vector<int>>& res) {
        res.push_back(path);
        for (int i = start; i < nums.size(); ++i) {
            path.push_back(nums[i]);
            backtrack(nums, i + 1, path, res);
            path.pop_back();
        }
    }
};
```