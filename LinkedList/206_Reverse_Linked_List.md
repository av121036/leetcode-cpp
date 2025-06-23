# 206. Reverse Linked List

## 題目描述

給定一個單向鏈結串列的頭節點 `head`，請反轉整個鏈結串列，並回傳新的頭節點。

---

## 範例

### Example 1:

```
輸入: head = [1,2,3,4,5]
輸出: [5,4,3,2,1]
```

### Example 2:

```
輸入: head = [1,2]
輸出: [2,1]
```

### Example 3:

```
輸入: head = []
輸出: []
```

---

## 解題想法

### 方法一：迴圈反轉

* 使用三個指標：`prev`、`curr`、`next`。
* 每次將 `curr->next` 指向 `prev`，然後將三個指標都往前移動。

---

## C++ 程式碼

```cpp
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode* prev = nullptr;
        ListNode* curr = head;
        while (curr) {
            ListNode* next = curr->next;
            curr->next = prev;
            prev = curr;
            curr = next;
        }
        return prev;
    }
};
```
