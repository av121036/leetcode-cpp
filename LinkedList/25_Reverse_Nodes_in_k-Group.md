# 25. Reverse Nodes in k-Group

## 題目描述

給定一個單向鏈結串列的頭節點 `head`，請你將每 `k` 個節點為一組進行反轉，並回傳修改後的鏈結串列。

如果節點總數不是 `k` 的倍數，則保留最後剩下的節點原順序不變。

你**只能使用常數級額外空間**，並且**不能改變節點的值**，只能修改節點指標。

---

## 範例

### Example 1:

```
輸入: head = [1,2,3,4,5], k = 2
輸出: [2,1,4,3,5]
```

### Example 2:

```
輸入: head = [1,2,3,4,5], k = 3
輸出: [3,2,1,4,5]
```

---

## 解題想法

1. 使用 dummy node 指向 head。
2. 使用 `pre`, `end` 兩指標：

   * `end` 移動 `k` 步找出當前段落。
   * 若不足 `k` 則跳出。
   * 記錄 `start = pre->next`，`next = end->next`。
3. 將 `start ~ end` 反轉後接回串列：

   * `pre->next = reverse(start)`
   * `start->next = next`
4. 更新 `pre = start`, `end = pre`'

---

## C++ 程式碼

```cpp
class Solution {
public:
    ListNode* reverseKGroup(ListNode* head, int k) {
        if (!head || k == 1) return head;
        ListNode dummy(0);
        dummy.next = head;
        ListNode* pre = &dummy;
        ListNode* end = &dummy;

        while (true) {
            for (int i = 0; i < k && end; ++i) end = end->next;
            if (!end) break;
            ListNode* start = pre->next;
            ListNode* next = end->next;
            end->next = nullptr;

            pre->next = reverse(start);
            start->next = next;
            pre = start;
            end = pre;
        }
        return dummy.next;
    }

private:
    ListNode* reverse(ListNode* head) {
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
