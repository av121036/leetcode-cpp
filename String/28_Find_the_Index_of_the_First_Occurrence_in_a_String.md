# 28. Find the Index of the First Occurrence in a String

## 題目描述

給定兩個字串 `haystack` 與 `needle`，請找出 `needle` 在 `haystack` 中第一次出現的索引位置，若未出現則回傳 -1。

如果 `needle` 是空字串，回傳 0。

---

## 範例

### Example 1:

```
輸入: haystack = "sadbutsad", needle = "sad"
輸出: 0
```

### Example 2:

```
輸入: haystack = "leetcode", needle = "leeto"
輸出: -1
```

---

## 解題想法

* 可以使用 `haystack.substr(i, needle.size())` 比對字串是否一致。
* 遍歷 `haystack` 每個可能起始點，直到 `n - m`（其中 `n = haystack.length()`，`m = needle.length()`）。
* 一旦找到對應子字串，回傳索引。
* 若走完整個 haystack 都沒找到，回傳 -1。

---

## C++ 程式碼

```cpp
class Solution {
public:
    int strStr(string haystack, string needle) {
        int n = haystack.size(), m = needle.size();
        if (m == 0) return 0;
        for (int i = 0; i <= n - m; ++i) {
            if (haystack.substr(i, m) == needle) {
                return i;
            }
        }
        return -1;
    }
};
```
