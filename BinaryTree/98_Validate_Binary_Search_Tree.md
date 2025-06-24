# 98\_Validate\_Binary\_Search\_Tree

## 題目描述

給定一棵二元樹，請判斷其是否為一棵**有效的二元搜尋樹（BST）**。

**定義：**

* 節點的左子樹只包含小於當前節點的數值
* 節點的右子樹只包含大於當前節點的數值
* 所有左子樹與右子樹也必須是二元搜尋樹

---

## 範例

### Example 1:

```
輸入: root = [2,1,3]
輸出: true
```

### Example 2:

```
輸入: root = [5,1,4,null,null,3,6]
輸出: false
說明: 根節點是 5，但右子樹有節點值為 3 < 5
```

---

## 解題想法

* 對每個節點傳遞其合法範圍：`(min, max)`
* 若節點不在此範圍內，則不是 BST

---

## C++ 程式碼

```cpp
class Solution {
public:
    bool isValidBST(TreeNode* root) {
        return helper(root, LONG_MIN, LONG_MAX);
    }

    bool helper(TreeNode* node, long minVal, long maxVal) {
        if (!node) return true;
        if (node->val <= minVal || node->val >= maxVal) return false;
        return helper(node->left, minVal, node->val) &&
               helper(node->right, node->val, maxVal);
    }
};
```
