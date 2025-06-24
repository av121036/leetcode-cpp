# 77\_Combinations

## 題目描述

給定兩個整數 `n` 和 `k`，請你回傳從 `1` 到 `n` 中取 `k` 個數字的所有組合。

你可以按任意順序回傳答案。

---

## 範例

### Example 1:

```
輸入: n = 4, k = 2
輸出: [
  [1,2],
  [1,3],
  [1,4],
  [2,3],
  [2,4],
  [3,4]
]
```

### Example 2:

```
輸入: n = 1, k = 1
輸出: [[1]]
```

---

## 解題想法

1. 每次從當前數字 `start` 開始遞迴下一層，避免重複。
2. 當組合長度等於 `k` 時，將其加入結果中。
3. 注意剪枝條件可提升效率：若 `剩下可選的數 < 還需要的數`，可以提前結束。

---

## C++ 程式碼

```cpp
class Solution {
public:
    vector<vector<int>> combine(int n, int k) {
        vector<vector<int>> res;
        vector<int> path;
        backtrack(1, n, k, path, res);
        return res;
    }

private:
    void backtrack(int start, int n, int k, vector<int>& path, vector<vector<int>>& res) {
        if (path.size() == k) {
            res.push_back(path);
            return;
        }
        for (int i = start; i <= n - (k - path.size()) + 1; ++i) {
            path.push_back(i);
            backtrack(i + 1, n, k, path, res);
            path.pop_back();
        }
    }
};
```

