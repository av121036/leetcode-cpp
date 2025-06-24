# 17. Letter Combinations of a Phone Number

## 題目描述

給定一個只包含數字 `2-9` 的字串，回傳所有它能表示的字母組合。

每個數字對應手機上的英文字母（與電話按鍵相同）。

你可以以任意順序回傳答案。

---

## 範例

### Example 1:

```
輸入: digits = "23"
輸出: ["ad","ae","af","bd","be","bf","cd","ce","cf"]
```

### Example 2:

```
輸入: digits = ""
輸出: []
```

### Example 3:

```
輸入: digits = "2"
輸出: ["a","b","c"]
```

---

## 解題想法

* 建立數字到字母的對應表（用陣列或 `unordered_map`）。
* 使用 DFS（遞迴）或 backtracking 遍歷所有組合。
* 若當前組合長度與輸入數字長度相同，即為有效組合。

---

## C++ 程式碼

```cpp
class Solution {
public:
    vector<string> letterCombinations(string digits) {
        if (digits.empty()) return {};
        vector<string> res;
        vector<string> mapping = {
            "",    "",    "abc",  "def",
            "ghi", "jkl", "mno",  "pqrs",
            "tuv", "wxyz"
        };
        string path;
        dfs(digits, 0, path, res, mapping);
        return res;
    }

private:
    void dfs(const string& digits, int index, string& path,
             vector<string>& res, vector<string>& mapping) {
        if (index == digits.size()) {
            res.push_back(path);
            return;
        }
        string letters = mapping[digits[index] - '0'];
        for (char c : letters) {
            path.push_back(c);
            dfs(digits, index + 1, path, res, mapping);
            path.pop_back();
        }
    }
};
```
