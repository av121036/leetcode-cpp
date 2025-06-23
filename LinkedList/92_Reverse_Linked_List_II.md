# 92. Reverse Linked List II

## 題目描述

給定一個單向鏈結串列的頭節點 `head`，與兩個整數 `left` 和 `right`，請你**只反轉從位置 `left` 到位置 `right` 的節點**（以 1 為起始索引），並回傳修改後的鏈結串列。

---

## 範例

### Example 1:

```
輸入: head = [1,2,3,4,5], left = 2, right = 4
輸出: [1,4,3,2,5]
```

### Example 2:

```
輸入: head = [5], left = 1, right = 1
輸出: [5]
```

---

## 解題想法

1. 使用 dummy node 指向 head，並找到 `left` 前一個節點 `pre`。
2. 使用 `cur` 開始進行 in-place 反轉，將 `cur->next` 插入到 `pre->next` 前面（頭插法）。
3. 重複執行 `right - left` 次，即可完成反轉。

---

## C++ 程式碼

```cpp
class Solution {
public:
    ListNode* reverseBetween(ListNode* head, int left, int right) {
        if (!head || left == right) return head;
        ListNode dummy(0);
        dummy.next = head;
        ListNode* pre = &dummy;
        for (int i = 1; i < left; ++i) {
            pre = pre->next;
        }
        ListNode* cur = pre->next;
        for (int i = 0; i < right - left; ++i) {
            ListNode* temp = cur->next;
            cur->next = temp->next;
            temp->next = pre->next;
            pre->next = temp;
        }
        return dummy.next;
    }
};
```

