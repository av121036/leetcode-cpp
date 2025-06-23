# 19. Remove Nth Node From End of List

## 題目描述

給定一個連結串列，請你刪除從尾部數來的第 `n` 個節點，並回傳修改後的頭節點。

---

## 範例

### Example 1:

```
輸入: head = [1,2,3,4,5], n = 2
輸出: [1,2,3,5]
```

### Example 2:

```
輸入: head = [1], n = 1
輸出: []
```

### Example 3:

```
輸入: head = [1,2], n = 1
輸出: [1]
```

---

## 解題想法

### 方法：雙指標（Two Pointers）

1. 使用兩個指標 `first` 和 `second`。
2. 先讓 `first` 往前走 `n+1` 步，保持與 `second` 間距為 `n`。
3. 然後同時移動 `first` 和 `second`，直到 `first` 為 `nullptr`。
4. 此時 `second` 所在位置就是要刪除節點的前一個節點。
5. 調整指標跳過該節點。

為了處理刪除頭節點的情況，使用 dummy 節點。

---

## C++ 程式碼

```cpp
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode* dummy = new ListNode(0);
        dummy->next = head;
        ListNode* first = dummy;
        ListNode* second = dummy;
        for (int i = 0; i <= n; ++i) {
            first = first->next;
        }
        while (first != nullptr) {
            first = first->next;
            second = second->next;
        }
        second->next = second->next->next;
        return dummy->next;
    }
};
```

---

## 備註

* dummy node（虛擬節點）技巧是處理頭節點刪除的常見方法。
