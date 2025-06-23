# 20. Valid Parentheses

題目連結：[LeetCode 20 - Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)

## 題目敘述

給定一個只包含 `()`、`[]`、`{}` 的字串，請判斷這個字串中的括號是否有效。

有效的括號必須符合：
1. 左括號必須由相同類型的右括號閉合。
2. 左括號必須以正確的順序閉合。

---

## 範例

- `Input`: `"()"`
- `Output`: `true`

- `Input`: `"()[]{}"`
- `Output`: `true`

- `Input`: `"(]"`
- `Output`: `false`

---

## 解題思路

1. 使用一個 **stack（堆疊）** 來儲存尚未配對的左括號。
2. 遇到左括號時，就 push 進 stack。
3. 遇到右括號時，檢查 stack 是否為空：
   - 若為空，代表沒有可配對的左括號，直接回傳 false。
   - 若不為空，就 pop 出 stack 最上層，判斷是否為對應的左括號。
4. 最後判斷 stack 是否為空，若為空代表所有括號都成功配對，回傳 true。

---

## C++ 程式碼

```cpp
class Solution {
public:
    bool isValid(string s) {
        stack<char> stk;
        for (char c : s) {
            if (c == '(') stk.push(')');
            else if (c == '{') stk.push('}');
            else if (c == '[') stk.push(']');
            else {
                if (stk.empty() || stk.top() != c) return false;
                stk.pop();
            }
        }
        return stk.empty();
    }
};
