# 387. First Unique Character in a String

## 題目描述

給定一個字串 `s`，請找出其中**第一個不重複字元**，並回傳它的索引。若沒有，則回傳 -1。

---

## 範例

### Example 1:

```
輸入: s = "leetcode"
輸出: 0
```

### Example 2:

```
輸入: s = "loveleetcode"
輸出: 2
```

### Example 3:

```
輸入: s = "aabb"
輸出: -1
```

---

## 解題想法

* 使用 `unordered_map<char, int>` 統計字元出現次數。
* 再次遍歷字串，找到第一個出現次數為 1 的字元。

---

## C++ 程式碼

```cpp
class Solution {
public:
    int firstUniqChar(string s) {
        unordered_map<char, int> freq;
        for (char c : s) {
            freq[c]++;
        }
        for (int i = 0; i < s.size(); ++i) {
            if (freq[s[i]] == 1) return i;
        }
        return -1;
    }
};
```