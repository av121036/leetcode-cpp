# 105\_Construct\_Binary\_Tree\_from\_Preorder\_and\_Inorder

## 題目描述

給定二元樹的前序遍歷（preorder）與中序遍歷（inorder）結果，請構造這棵樹並回傳其根節點。

**你可以假設所有節點的值都是唯一的。**

---

## 範例

### Example 1:

```
輸入:
preorder = [3,9,20,15,7]
inorder = [9,3,15,20,7]
輸出:
    3
   / \
  9  20
     /  \
    15   7
```

### Example 2:

```
輸入:
preorder = [-1]
inorder = [-1]
輸出: 單一節點的樹
```

---

## 解題想法

* 前序的第一個元素是「當前子樹的根」
* 在中序中找到根的位置，可劃分左右子樹的 inorder 區間
* 遞迴建立左右子樹

### 注意：

* 遍歷 preorder 時，從左至右（根 -> 左 -> 右）
* 用 hashmap 儲存 inorder 中每個值的索引，加速查找

---

## C++ 程式碼

```cpp
class Solution {
public:
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        unordered_map<int, int> inMap;
        for (int i = 0; i < inorder.size(); ++i) {
            inMap[inorder[i]] = i;
        }

        int preIndex = 0;
        return build(preorder, inorder, 0, inorder.size() - 1, preIndex, inMap);
    }

    TreeNode* build(vector<int>& preorder, vector<int>& inorder, int inStart, int inEnd, int& preIndex, unordered_map<int, int>& inMap) {
        if (inStart > inEnd) return nullptr;

        int rootVal = preorder[preIndex++];
        TreeNode* root = new TreeNode(rootVal);

        int inRoot = inMap[rootVal];

        root->left = build(preorder, inorder, inStart, inRoot - 1, preIndex, inMap);
        root->right = build(preorder, inorder, inRoot + 1, inEnd, preIndex, inMap);

        return root;
    }
};
```