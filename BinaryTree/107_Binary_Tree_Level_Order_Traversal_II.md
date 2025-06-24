# 107\_Binary\_Tree\_Level\_Order\_Traversal\_II

## 題目描述

給定一個二元樹，返回其節點值的「自底向上」層序遍歷（即從葉子節點所在層到根節點所在層，逐層從左到右遍歷）。

---

## 範例

### Example:

```
輸入: root = [3,9,20,null,null,15,7]
輸出: [[15,7],[9,20],[3]]
```

---

## 解題想法

可以採用 BFS（廣度優先搜尋）逐層遍歷：

1. 使用 queue 將節點逐層放入
2. 每層的節點值存入一個 vector
3. 最後將所有層的 vector「反轉」即可得到自底向上的順序

---

## C++ 程式碼

```cpp
class Solution {
public:
    vector<vector<int>> levelOrderBottom(TreeNode* root) {
        vector<vector<int>> result;
        if (!root) return result;

        queue<TreeNode*> q;
        q.push(root);

        while (!q.empty()) {
            int levelSize = q.size();
            vector<int> level;

            for (int i = 0; i < levelSize; ++i) {
                TreeNode* node = q.front(); q.pop();
                level.push_back(node->val);
                if (node->left) q.push(node->left);
                if (node->right) q.push(node->right);
            }

            result.push_back(level);
        }

        reverse(result.begin(), result.end());
        return result;
    }
};
```