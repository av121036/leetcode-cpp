# 108\_Convert\_Sorted\_Array\_to\_BST

## 題目描述

給定一個**遞增排序**的整數陣列 `nums`，請你將其轉換為一棵**高度平衡的二元搜尋樹（BST）**。

**高度平衡**的定義是：一棵二元樹中，每個節點的左右兩個子樹的高度差不超過 1。

---

## 範例

### Example:

```
輸入: nums = [-10,-3,0,5,9]
輸出: [0,-3,9,-10,null,5]

輸出結果為其中一棵滿足條件的 BST：
      0
     / \
   -3   9
   /   /
 -10  5
```

---

## 解題想法


1. 將陣列中間的元素作為根節點（中間偏左或偏右皆可）
2. 左半部分遞迴構建左子樹
3. 右半部分遞迴構建右子樹

這樣保證左右子樹大小差不超過 1，符合「高度平衡」的要求。


---

## C++ 程式碼

```cpp
class Solution {
public:
    TreeNode* sortedArrayToBST(vector<int>& nums) {
        return build(nums, 0, nums.size() - 1);
    }

    TreeNode* build(vector<int>& nums, int left, int right) {
        if (left > right) return nullptr;

        int mid = left + (right - left) / 2;
        TreeNode* root = new TreeNode(nums[mid]);
        root->left = build(nums, left, mid - 1);
        root->right = build(nums, mid + 1, right);
        return root;
    }
};
```