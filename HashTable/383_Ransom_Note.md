# 383. Ransom Note

## 題目描述

給定兩個字串 `ransomNote` 與 `magazine`，請判斷 `ransomNote` 是否可以由 `magazine` 中的字母構成。

每個 `magazine` 中的字母只能被使用一次。

---

## 範例

### Example 1:

```
輸入: ransomNote = "a", magazine = "b"
輸出: false
```

### Example 2:

```
輸入: ransomNote = "aa", magazine = "ab"
輸出: false
```

### Example 3:

```
輸入: ransomNote = "aa", magazine = "aab"
輸出: true
```

---

## 解題想法

* 使用 `array<int, 26>` 或 `unordered_map<char, int>` 統計 `magazine` 中各字母出現的次數。
* 遍歷 `ransomNote`，對每個字母進行扣減：

  * 若某字母次數已為 0 或不足，則回傳 `false`。
* 若全部字母都可成功配對，回傳 `true`。

時間複雜度：`O(n)`
空間複雜度：`O(1)`（只針對小寫英文字母）

---

## C++ 程式碼

```cpp
class Solution {
public:
    bool canConstruct(string ransomNote, string magazine) {
        array<int, 26> count = {0};
        for (char c : magazine) count[c - 'a']++;
        for (char c : ransomNote) {
            if (--count[c - 'a'] < 0) return false;
        }
        return true;
    }
};
```

---

## 備註

* 與 242 類似，但此題的字母來源只允許使用一次。
