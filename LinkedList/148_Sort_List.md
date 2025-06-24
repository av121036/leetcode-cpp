# 148. Sort List

## 題目描述

給定一個單向鏈結串列的頭節點 `head`，請對其進行排序，並回傳排序後的鏈結串列。

要求時間複雜度為 `O(n log n)`，且使用常數級空間（不算遞迴棧空間）。

---

## 範例

### Example 1:

```
輸入: head = [4,2,1,3]
輸出: [1,2,3,4]
```

### Example 2:

```
輸入: head = [-1,5,3,4,0]
輸出: [-1,0,3,4,5]
```

### Example 3:

```
輸入: head = []
輸出: []
```

---

## 解題想法

使用 merge sort：

1. 將鏈結串列以快慢指標方式切成兩半：

   * 使用 `slow` 和 `fast` 指標找到中點。
2. 遞迴對左右半部進行排序。
3. 使用合併兩有序串列（merge two sorted lists）的邏輯合併結果。

---

## C++ 程式碼

```cpp
class Solution {
public:
    ListNode* sortList(ListNode* head) {
        if (!head || !head->next) return head;

        // 分割：找中點
        ListNode* slow = head;
        ListNode* fast = head->next;
        while (fast && fast->next) {
            slow = slow->next;
            fast = fast->next->next;
        }
        ListNode* mid = slow->next;
        slow->next = nullptr;

        // 遞迴排序左右兩半
        ListNode* left = sortList(head);
        ListNode* right = sortList(mid);

        // 合併排序好的兩半
        return merge(left, right);
    }

private:
    ListNode* merge(ListNode* l1, ListNode* l2) {
        ListNode dummy(0);
        ListNode* tail = &dummy;
        while (l1 && l2) {
            if (l1->val < l2->val) {
                tail->next = l1;
                l1 = l1->next;
            } else {
                tail->next = l2;
                l2 = l2->next;
            }
            tail = tail->next;
        }
        tail->next = l1 ? l1 : l2;
        return dummy.next;
    }
};
```
