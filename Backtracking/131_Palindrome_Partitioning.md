# 131\_Palindrome\_Partitioning

## 題目描述

給定一個字串 `s`，將其拆分成所有可能的**回文子字串**組合，使得每個子字串皆為回文。

回傳所有可能的拆分結果。

---

## 範例

### Example 1:

```
輸入: s = "aab"
輸出: [["a","a","b"],["aa","b"]]
```

### Example 2:

```
輸入: s = "a"
輸出: [["a"]]
```

---

## 解題想法

1. 使用 `start` 指標來控制切割位置。
2. 每當發現 `s[start...i]` 是回文時，就可以切一段，繼續往後切。
3. 當 `start == s.length()` 表示切到尾巴，加入結果。

使用輔助函式 `isPalindrome(s, left, right)` 實作回文判斷。

---

## C++ 程式碼

```cpp
class Solution {
public:
    vector<vector<string>> partition(string s) {
        vector<vector<string>> res;
        vector<string> path;
        backtrack(s, 0, path, res);
        return res;
    }

private:
    void backtrack(const string& s, int start,
                   vector<string>& path, vector<vector<string>>& res) {
        if (start == s.size()) {
            res.push_back(path);
            return;
        }
        for (int i = start; i < s.size(); ++i) {
            if (isPalindrome(s, start, i)) {
                path.push_back(s.substr(start, i - start + 1));
                backtrack(s, i + 1, path, res);
                path.pop_back();
            }
        }
    }

    bool isPalindrome(const string& s, int left, int right) {
        while (left < right) {
            if (s[left++] != s[right--]) return false;
        }
        return true;
    }
};
```
