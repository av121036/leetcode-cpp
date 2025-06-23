# 203. Remove Linked List Elements

## 題目描述

給定一個鏈結串列的頭節點 `head` 和一個整數 `val`，請刪除所有節點值等於 `val` 的節點，並回傳新的頭節點。

---

## 範例

### Example 1:

```
輸入: head = [1,2,6,3,4,5,6], val = 6
輸出: [1,2,3,4,5]
```

### Example 2:

```
輸入: head = [], val = 1
輸出: []
```

### Example 3:

```
輸入: head = [7,7,7,7], val = 7
輸出: []
```

---

## 解題想法

* 使用 dummy node 處理頭節點被刪除的情況。
* 使用一個指標 `curr` 從 dummy 開始遍歷。
* 若 `curr->next->val == val`，就跳過該節點。
* 否則繼續移動。

---

## C++ 程式碼

```cpp
class Solution {
public:
    ListNode* removeElements(ListNode* head, int val) {
        ListNode dummy(0);
        dummy.next = head;
        ListNode* curr = &dummy;
        while (curr->next) {
            if (curr->next->val == val) {
                curr->next = curr->next->next;
            } else {
                curr = curr->next;
            }
        }
        return dummy.next;
    }
};
```

