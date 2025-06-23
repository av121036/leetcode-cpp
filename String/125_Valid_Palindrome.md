# 125. Valid Palindrome

## 題目描述

給定一個字串 `s`，請判斷其是否為「回文串」。

只考慮字母與數字，忽略大小寫。

---

## 範例

### Example 1:

```
輸入: s = "A man, a plan, a canal: Panama"
輸出: true
解釋: "amanaplanacanalpanama" 是回文
```

### Example 2:

```
輸入: s = "race a car"
輸出: false
```

---

## 解題想法

* 使用雙指標，從左右兩端往中間檢查。
* 忽略非英數字元（使用 `isalnum()`）。
* 忽略大小寫（使用 `tolower()`）。
* 若對應位置不一致則回傳 false。

時間複雜度：`O(n)`
空間複雜度：`O(1)`（不需額外儲存字串）

---

## C++ 程式碼

```cpp
class Solution {
public:
    bool isPalindrome(string s) {
        int left = 0, right = s.size() - 1;
        while (left < right) {
            while (left < right && !isalnum(s[left])) ++left;
            while (left < right && !isalnum(s[right])) --right;
            if (tolower(s[left]) != tolower(s[right])) return false;
            ++left;
            --right;
        }
        return true;
    }
};
```

---

## 備註

* `isalnum()` 檢查是否為字母或數字
* `tolower()` 處理大小寫一致性