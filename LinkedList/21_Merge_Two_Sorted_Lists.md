# 21. Merge Two Sorted Lists

## 題目描述

給定兩個升序排序的鏈結串列 `list1` 和 `list2`，請合併它們為一個新的**升序**鏈結串列，並回傳這個新串列的頭節點。

---

## 範例

### Example 1:

```
輸入: list1 = [1,2,4], list2 = [1,3,4]
輸出: [1,1,2,3,4,4]
```

### Example 2:

```
輸入: list1 = [], list2 = []
輸出: []
```

### Example 3:

```
輸入: list1 = [], list2 = [0]
輸出: [0]
```

---

## 解題想法

* 使用 dummy 節點建立新串列。
* 指標 `tail` 指向目前串列的末端。
* 比較 `list1` 與 `list2` 當前節點大小，將較小者接到 `tail` 後面。
* 移動對應節點與 `tail`，直到其中一個串列為空。
* 最後將剩下未空的串列接上。

---

## C++ 程式碼

```cpp
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        ListNode dummy(0);
        ListNode* tail = &dummy;
        while (list1 && list2) {
            if (list1->val < list2->val) {
                tail->next = list1;
                list1 = list1->next;
            } else {
                tail->next = list2;
                list2 = list2->next;
            }
            tail = tail->next;
        }
        tail->next = list1 ? list1 : list2;
        return dummy.next;
    }
};
```
