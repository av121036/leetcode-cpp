# 104\_Maximum\_Depth\_of\_Binary\_Tree

## 題目描述

給定一棵二元樹，找出其**最大深度**。

最大深度是從根節點到最遠葉子節點的最長路徑上的節點數。

---

## 範例

### Example 1:

```
輸入: root = [3,9,20,null,null,15,7]
輸出: 3
```

### Example 2:

```
輸入: root = [1,null,2]
輸出: 2
```

---

## 解題想法

使用 **遞迴 DFS** 或 **BFS 層序遍歷** 均可。

遞迴方式簡潔且直觀：

* 若節點為 null，回傳 0
* 否則回傳左右子樹最大深度 + 1

---

## C++ 程式碼

```cpp
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if (!root) return 0;
        return 1 + max(maxDepth(root->left), maxDepth(root->right));
    }
};
```