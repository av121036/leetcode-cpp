# 345. Reverse Vowels of a String

## 題目描述

給定一個字串 `s`，只反轉其中的母音字元，並回傳結果。

母音包含 `'a'`, `'e'`, `'i'`, `'o'`, `'u'` 以及其大寫對應字元。

---

## 範例

### Example 1:

```
輸入: s = "hello"
輸出: "holle"
```

### Example 2:

```
輸入: s = "leetcode"
輸出: "leotcede"
```

---

## 解題想法

* 使用雙指標 `left` 和 `right`。
* 若 `s[left]` 非母音，左指標右移；若 `s[right]` 非母音，右指標左移。
* 若兩者皆為母音，則交換後繼續移動。

---

## C++ 程式碼

```cpp
class Solution {
public:
    string reverseVowels(string s) {
        unordered_set<char> vowels = {'a','e','i','o','u','A','E','I','O','U'};
        int left = 0, right = s.size() - 1;
        while (left < right) {
            while (left < right && !vowels.count(s[left])) ++left;
            while (left < right && !vowels.count(s[right])) --right;
            if (left < right) {
                swap(s[left++], s[right--]);
            }
        }
        return s;
    }
};
```

---

## 備註

* 使用 `unordered_set` 加速母音判斷。
* 本題是 344 的進階版，增加了條件限制。
