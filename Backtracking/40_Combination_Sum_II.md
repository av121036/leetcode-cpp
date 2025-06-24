# 40\_Combination\_Sum\_II

## 題目描述

給定一個可能包含重複數字的整數陣列 `candidates` 和一個目標值 `target`，找出所有「**不重複的組合**」，使得組合中數字加總為 `target`。**每個數字只能使用一次**。

你可以按任意順序回傳答案。

---

## 範例

### Example 1:

```
輸入: candidates = [10,1,2,7,6,1,5], target = 8
輸出: [
  [1,1,6],
  [1,2,5],
  [1,7],
  [2,6]
]
```

### Example 2:

```
輸入: candidates = [2,5,2,1,2], target = 5
輸出: [
  [1,2,2],
  [5]
]
```

---

## 解題思路

這題是 39 題的變形：

* 每個數只能使用一次（`i + 1` 取代 `i`）。
* 有重複數字，因此需「先排序」並「跳過重複元素」。

跳過條件：

```cpp
if (i > start && candidates[i] == candidates[i - 1]) continue;
```
---

## C++ 程式碼

```cpp
class Solution {
public:
    vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
        vector<vector<int>> res;
        vector<int> path;
        sort(candidates.begin(), candidates.end());
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
        for (int i = start; i < candidates.size(); ++i) {
            if (i > start && candidates[i] == candidates[i - 1]) continue;
            if (candidates[i] > target) break;
            path.push_back(candidates[i]);
            backtrack(candidates, target - candidates[i], i + 1, path, res); // 每個數只能用一次
            path.pop_back();
        }
    }
};
```