# LeetCode 練習：02_Sort_2D_Array（二維陣列排序）

## 📝 題目說明

給定一個二維整數陣列，請將每一列（row）依序從小到大排序。
這題可以幫助你理解如何操作二維 `vector`，並應用排序技巧。

---

## ✅ 範例輸入

```
輸入:
[
  [3, 2, 1],
  [9, 5, 6],
  [7, 8, 4]
]

輸出:
[
  [1, 2, 3],
  [5, 6, 9],
  [4, 7, 8]
]
```

---

## 🧠 解法解析

- 使用 `vector<vector<int>>` 來建立二維陣列
- 使用 `sort()` 搭配 `begin()` 和 `end()` 針對每一列做排序

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main() {
    vector<vector<int>> matrix = {
        {3, 2, 1},
        {9, 5, 6},
        {7, 8, 4}
    };

    // 使用 index-based 方式排序每一列
    for (int i = 0; i < matrix.size(); i++) {
        sort(matrix[i].begin(), matrix[i].end());
    }

    // 輸出排序後的二維陣列
    for (int i = 0; i < matrix.size(); i++) {
        for (int j = 0; j < matrix[i].size(); j++) {
            cout << matrix[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}
```

---
