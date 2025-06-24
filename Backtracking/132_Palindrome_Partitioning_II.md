# 132\_Palindrome\_Partitioning\_II

## 題目描述

給定一個字串 `s`，將其切割成若干個回文子字串，使得「切割的次數最少」。

回傳這個最少切割的次數。

---

## 範例

### Example 1:

```
輸入: s = "aab"
輸出: 1
解釋: 將 "aab" 切割成 ["aa","b"]，只需 1 次切割。
```

### Example 2:

```
輸入: s = "a"
輸出: 0
```

### Example 3:

```
輸入: s = "ab"
輸出: 1
```

---

## 解題想法

目標是找到「讓每段皆為回文」的最小切割次數。

1. 建立 `isPalindrome[i][j]` 陣列來記錄 s\[i..j] 是否為回文。
2. 使用 `dp[i]` 表示 `s[0..i]` 最少需要幾次切割：

   * 如果 `s[0..i]` 是回文，則 `dp[i] = 0`
   * 否則找最小的 `dp[j] + 1`，其中 `s[j+1..i]` 是回文

---

## C++ 程式碼

```cpp
class Solution {
public:
    int minCut(string s) {
        int n = s.size();
        vector<vector<bool>> isPalindrome(n, vector<bool>(n, false));

        // 建立回文表
        for (int end = 0; end < n; ++end) {
            for (int start = 0; start <= end; ++start) {
                if (s[start] == s[end] && (end - start <= 2 || isPalindrome[start + 1][end - 1])) {
                    isPalindrome[start][end] = true;
                }
            }
        }

        vector<int> dp(n, INT_MAX);

        for (int i = 0; i < n; ++i) {
            if (isPalindrome[0][i]) {
                dp[i] = 0;
            } else {
                for (int j = 0; j < i; ++j) {
                    if (isPalindrome[j + 1][i]) {
                        dp[i] = min(dp[i], dp[j] + 1);
                    }
                }
            }
        }

        return dp[n - 1];
    }
};
```
