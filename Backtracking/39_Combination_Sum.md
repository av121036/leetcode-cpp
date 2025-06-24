# 39\_Combination\_Sum

## 題目描述

給定一個無重複元素的正整數陣列 `candidates` 和一個目標值 `target`，找出所有「**元素可以重複選取**」的組合，使其總和等於 `target`。

你可以按任意順序回傳答案。

---

## 範例

### Example 1:

```
輸入: candidates = [2,3,6,7], target = 7
輸出: [[2,2,3],[7]]
```

### Example 2:

```
輸入: candidates = [2,3,5], target = 8
輸出: [[2,2,2,2],[2,3,3],[3,5]]
```

### Example 3:

```
輸入: candidates = [2], target = 1
輸出: []
```

---

## 解題想法

1. 每次遞迴可以重複選取當前數字（所以 `i` 不變）。
2. 若目前總和大於 `target` 則剪枝。
3. 當總和等於 `target` 時，記錄下目前組合。

---

## C++ 程式碼

```cpp
class Solution {
public:
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        vector<vector<int>> res;
        vector<int> path;
        backtrack(candidates, target, 0, path, res);
        return res;
    }

private:
    void backtrack(vector<int>& candidates, int target, int start,
                   vector<int>& path, vector<vector<int>>& res) {
        if (target == 0) {
            res.push_back(path);
            return;
        }
        if (target < 0) return;
        for (int i = start; i < candidates.size(); ++i) {
            path.push_back(candidates[i]);
            backtrack(candidates, target - candidates[i], i, path, res); // 可重複選取
            path.pop_back();
        }
    }
};
```
