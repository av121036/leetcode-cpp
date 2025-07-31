# 56\_Merge\_Intervals

## ⭐ 題目描述 (Merge Intervals)

給定一個區間的陣列 `intervals`，其中每個區間表示為 `[start, end]`。

請合併所有**重疊**的區間，並回傳**不重疊區間的集合**（任意順序均可）。

### 範例

```text
輸入: intervals = [[1,3],[2,6],[8,10],[15,18]]
輸出: [[1,6],[8,10],[15,18]]
解釋: [1,3] 和 [2,6] 重疊，合併成 [1,6]

輸入: intervals = [[1,4],[4,5]]
輸出: [[1,5]]
```

---

## 🧰 解題思路：排序 + 合併

1. 將區間依照起點 `start` 排序。
2. 使用一個 `result` 陣列來存放合併後的結果。
3. 遍歷每個區間：
   - 如果 `result` 為空，或當前區間的起點 `start` > 前一個區間的結束 `end`，代表不重疊，直接加入。
   - 否則，更新前一個區間的結束點為：`max(end, current_end)`（合併）。

---

## ✅ C++ 解法

```cpp
#include <vector>
#include <algorithm>
using namespace std;

vector<vector<int>> merge(vector<vector<int>>& intervals) {
    if (intervals.empty()) return {};

    // 先依照起點排序
    sort(intervals.begin(), intervals.end());
    
    vector<vector<int>> merged;
    merged.push_back(intervals[0]);

    for (int i = 1; i < intervals.size(); ++i) {
        vector<int>& last = merged.back();
        vector<int>& current = intervals[i];

        if (current[0] <= last[1]) {
            // 重疊：更新結尾
            last[1] = max(last[1], current[1]);
        } else {
            // 不重疊：加入新區間
            merged.push_back(current);
        }
    }

    return merged;
}
```

---
## 🧠 小提醒

- 重點是**排序 + 比較**，先排序可以讓所有重疊區間排列在一起。
- `sort(intervals.begin(), intervals.end())` 預設會以第一個元素做排序。

