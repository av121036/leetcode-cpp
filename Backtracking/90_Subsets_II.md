# 90\_Subsets\_II

## 題目描述

給定一個可能包含重複元素的整數陣列 `nums`，請你回傳所有可能的子集（potentail subsets，**幂集**）。

**解集不能包含重複的子集。**

你可以按任意順序回傳答案。

---

## 範例

### Example 1:

```
輸入: nums = [1,2,2]
輸出: [
  [2],
  [1],
  [1,2,2],
  [2,2],
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

* **先排序**，讓重複元素相鄰。
* **跳過相同層的重複元素**：

```cpp
if (i > start && nums[i] == nums[i - 1]) continue;
```

## C++ 程式碼

```cpp
class Solution {
public:
    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
        vector<vector<int>> res;
        vector<int> path;
        sort(nums.begin(), nums.end());
        backtrack(nums, 0, path, res);
        return res;
    }

private:
    void backtrack(vector<int>& nums, int start, vector<int>& path,
                   vector<vector<int>>& res) {
        res.push_back(path);
        for (int i = start; i < nums.size(); ++i) {
            if (i > start && nums[i] == nums[i - 1]) continue;
            path.push_back(nums[i]);
            backtrack(nums, i + 1, path, res);
            path.pop_back();
        }
    }
};
```
