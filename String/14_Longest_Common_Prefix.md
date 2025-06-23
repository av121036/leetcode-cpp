# 14. Longest Common Prefix

## 題目描述

編寫一個函式，找出字串陣列 `strs` 中的最長共同前綴字串。

如果不存在共同前綴，回傳空字串 `""`。

---

## 範例

### Example 1:

```
輸入: strs = ["flower","flow","flight"]
輸出: "fl"
```

### Example 2:

```
輸入: strs = ["dog","racecar","car"]
輸出: ""
解釋: 沒有共同前綴。
```

---

## 解題想法

* 方法一：逐字比較

  1. 以第一個字串為基準，遍歷每個字元位置。
  2. 檢查其他字串在該位置是否相同。
  3. 若有不同則回傳目前為止的前綴。

---

## C++ 程式碼

```cpp
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        if (strs.empty()) return "";
        for (int i = 0; i < strs[0].size(); ++i) {
            char c = strs[0][i];
            for (int j = 1; j < strs.size(); ++j) {
                if (i >= strs[j].size() || strs[j][i] != c) {
                    return strs[0].substr(0, i);
                }
            }
        }
        return strs[0];
    }
};
```

