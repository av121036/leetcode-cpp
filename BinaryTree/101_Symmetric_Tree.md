# 101\_Symmetric\_Tree

## 題目描述

給定一棵二元樹，檢查它是否為**對稱二元樹**（鏡像樹）。

---

## 範例

### Example 1:

```
輸入: root = [1,2,2,3,4,4,3]
輸出: true
```

### Example 2:

```
輸入: root = [1,2,2,null,3,null,3]
輸出: false
```

---

## 解題想法

這題可以看成「兩棵樹是否為鏡像」的問題。

定義一個遞迴函式 `isMirror(TreeNode* t1, TreeNode* t2)`：

* 若兩節點都為 null：回傳 true
* 若一個為 null 或兩者值不同：回傳 false
* 否則比較：

  * `t1->left` 與 `t2->right` 是否鏡像
  * `t1->right` 與 `t2->left` 是否鏡像

---

## C++ 程式碼

```cpp
class Solution {
public:
    bool isSymmetric(TreeNode* root) {
        return isMirror(root, root);
    }

    bool isMirror(TreeNode* t1, TreeNode* t2) {
        if (!t1 && !t2) return true;
        if (!t1 || !t2 || t1->val != t2->val) return false;
        return isMirror(t1->left, t2->right) && isMirror(t1->right, t2->left);
    }
};
```