# 242. Valid Anagram

## 題目描述

給定兩個字串 `s` 和 `t`，請判斷 `t` 是否為 `s` 的字母重組（anagram）。

即兩字串的所有字母數量都相同，但順序可以不同。

---

## 範例

### Example 1:

```
輸入: s = "anagram", t = "nagaram"
輸出: true
```

### Example 2:

```
輸入: s = "rat", t = "car"
輸出: false
```

---

## 解題想法

* 使用 `unordered_map<char, int>` 統計字串 `s` 中每個字母的出現次數。
* 遍歷 `t`，對應的字母計數減一。
* 最後確認 map 中所有字母的計數是否都為 0。

或者，也可以使用 `array<int, 26>` 優化空間與速度（只處理小寫英文字母）。

---

## C++ 程式碼

```cpp
class Solution {
public:
    bool isAnagram(string s, string t) {
        if (s.length() != t.length()) return false;
        array<int, 26> count = {0};
        for (char c : s) count[c - 'a']++;
        for (char c : t) {
            if (--count[c - 'a'] < 0) return false;
        }
        return true;
    }
};
```
