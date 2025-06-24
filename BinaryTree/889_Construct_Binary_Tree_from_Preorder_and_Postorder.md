# 889\_Construct\_Binary\_Tree\_from\_Preorder\_and\_Postorder

## 題目描述

給定二元樹的\*\*前序遍歷（preorder）**與**後序遍歷（postorder）\*\*結果，請構造這棵樹。

**注意：**

* 可以保證對於給定的輸入，至少存在一棵符合條件的二元樹。
* 你可以返回其中任意一棵符合條件的樹。

---

## 範例

### Example 1:

```
輸入:
preorder = [1,2,4,5,3,6,7]
postorder = [4,5,2,6,7,3,1]
輸出:
        1
       / \
      2   3
     / \ / \
    4  5 6  7
```

---

## 解題想法

這題無法唯一構造一棵樹，因為缺少中序資訊，但仍可透過遞迴構造**一棵合法解**。

1. 前序的第一個元素為根節點 `root`
2. 第二個元素是左子樹的根 `leftRoot`
3. 在後序遍歷中找到 `leftRoot` 的索引 `idx`
4. 計算左子樹的長度 `L = idx - postStart + 1`
5. 遞迴構造左右子樹

---

## C++ 程式碼

```cpp
class Solution {
public:
    TreeNode* constructFromPrePost(vector<int>& preorder, vector<int>& postorder) {
        unordered_map<int, int> postMap;
        for (int i = 0; i < postorder.size(); ++i) {
            postMap[postorder[i]] = i;
        }
        return build(preorder, postorder, 0, preorder.size() - 1, 0, postorder.size() - 1, postMap);
    }

    TreeNode* build(vector<int>& pre, vector<int>& post, int preStart, int preEnd, int postStart, int postEnd, unordered_map<int, int>& postMap) {
        if (preStart > preEnd) return nullptr;
        TreeNode* root = new TreeNode(pre[preStart]);
        if (preStart == preEnd) return root;

        int leftRootVal = pre[preStart + 1];
        int idx = postMap[leftRootVal];
        int leftSize = idx - postStart + 1;

        root->left = build(pre, post, preStart + 1, preStart + leftSize, postStart, idx, postMap);
        root->right = build(pre, post, preStart + leftSize + 1, preEnd, idx + 1, postEnd - 1, postMap);

        return root;
    }
};
```
