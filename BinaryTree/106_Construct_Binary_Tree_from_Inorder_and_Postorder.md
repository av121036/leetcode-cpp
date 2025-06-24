# 106\_Construct\_Binary\_Tree\_from\_Inorder\_and\_Postorder

## 題目描述

給定二元樹的中序遍歷（inorder）與後序遍歷（postorder）結果，請構造這棵樹並回傳其根節點。

**你可以假設所有節點的值都是唯一的。**

---

## 範例

### Example 1:

```
輸入:
inorder = [9,3,15,20,7]
postorder = [9,15,7,20,3]
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
inorder = [-1]
postorder = [-1]
輸出: 單一節點的樹
```

---

## 解題想法

* 後序的最後一個元素是「當前子樹的根」
* 在中序中找到根的位置，可分出左右子樹的範圍
* 遞迴地構造左右子樹即可

---

## C++ 程式碼

```cpp
class Solution {
public:
    TreeNode* buildTree(vector<int>& inorder, vector<int>& postorder) {
        unordered_map<int, int> inMap;
        for (int i = 0; i < inorder.size(); ++i) {
            inMap[inorder[i]] = i;
        }

        int postIndex = postorder.size() - 1;
        return build(inorder, postorder, 0, inorder.size() - 1, postIndex, inMap);
    }

    TreeNode* build(vector<int>& inorder, vector<int>& postorder, int inStart, int inEnd, int& postIndex, unordered_map<int, int>& inMap) {
        if (inStart > inEnd) return nullptr;

        int rootVal = postorder[postIndex--];
        TreeNode* root = new TreeNode(rootVal);

        int inRoot = inMap[rootVal];

        // 注意：先建立右子樹，再左子樹（因為 postorder 是 左->右->根）
        root->right = build(inorder, postorder, inRoot + 1, inEnd, postIndex, inMap);
        root->left = build(inorder, postorder, inStart, inRoot - 1, postIndex, inMap);

        return root;
    }
};
```
