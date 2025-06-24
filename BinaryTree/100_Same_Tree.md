# 100\_Same\_Tree

## 題目描述

給定兩棵二元樹 `p` 和 `q`，請檢查它們是否**相同**。

兩棵樹被視為相同，當它們的結構相同，且對應節點的值也相同。

---

## 範例

### Example 1:

```
輸入:
p = [1,2,3], q = [1,2,3]
輸出: true
```

### Example 2:

```
輸入:
p = [1,2], q = [1,null,2]
輸出: false
```

### Example 3:

```
輸入:
p = [1,2,1], q = [1,1,2]
輸出: false
```

---

## 解題想法

使用 **遞迴** 方法遍歷兩棵樹，依序比較：

1. 若 `p` 與 `q` 都為 `nullptr`，回傳 `true`
2. 若一邊為 `nullptr` 或數值不同，回傳 `false`
3. 否則遞迴比較左右子樹是否相同

---

## C++ 程式碼

```cpp
class Solution {
public:
    bool isSameTree(TreeNode* p, TreeNode* q) {
        if (!p && !q) return true;
        if (!p || !q || p->val != q->val) return false;
        return isSameTree(p->left, q->left) && isSameTree(p->right, q->right);
    }
};
```
