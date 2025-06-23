# 49. Group Anagrams

## 題目描述

給定一個字串陣列 `strs`，請將所有是字母重組（Anagram）的字串分組。

你可以以任意順序回傳答案。

---

## 範例

### Example 1:

```
輸入: strs = ["eat", "tea", "tan", "ate", "nat", "bat"]
輸出: [["eat","tea","ate"],["tan","nat"],["bat"]]
```

### Example 2:

```
輸入: strs = [""]
輸出: [[""]]
```

### Example 3:

```
輸入: strs = ["a"]
輸出: [["a"]]
```

---

## 解題想法

* 使用 `unordered_map<string, vector<string>>`：

  * 對每個字串進行排序，作為 key。
  * 相同排序結果的字串即為 Anagram，將它們歸到同一個 vector 中。

* 最後將 map 的所有 value（vector<string>）回傳。

---

## C++ 程式碼

```cpp
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        unordered_map<string, vector<string>> map;
        for (string s : strs) {
            string key = s;
            sort(key.begin(), key.end());
            map[key].push_back(s);
        }
        vector<vector<string>> result;
        for (auto& pair : map) {
            result.push_back(pair.second);
        }
        return result;
    }
};
```