# 109\_Convert\_Sorted\_List\_to\_BST

## 題目描述

給定一個**遞增排序的單向連結串列**，請將其轉換為一棵**高度平衡的二元搜尋樹（BST）**。

---

## 範例

### Example:

```
輸入: head = [-10,-3,0,5,9]
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

1. 用 slow / fast pointer 找出中間節點作為 root
2. 將左半部分與右半部分遞迴轉成子樹
3. 注意要斷開 left list 結尾（需儲存前一節點）


---

## C++ 程式碼

```cpp
class Solution {
public:
    TreeNode* sortedListToBST(ListNode* head) {
        if (!head) return nullptr;
        if (!head->next) return new TreeNode(head->val);

        ListNode* prev = nullptr;
        ListNode* slow = head;
        ListNode* fast = head;

        // 快慢指標找中點
        while (fast && fast->next) {
            prev = slow;
            slow = slow->next;
            fast = fast->next->next;
        }

        if (prev) prev->next = nullptr; // 斷開 left 子串

        TreeNode* root = new TreeNode(slow->val);
        root->left = sortedListToBST((prev ? head : nullptr));
        root->right = sortedListToBST(slow->next);

        return root;
    }
};
```