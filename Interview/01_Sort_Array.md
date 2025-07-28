# LeetCode 練習：01_Sort_Array（將陣列由小到大排序）

## 📝 題目說明

將一個整數陣列進行排序，從小到大排列。這是一題基本題，目的是讓你熟悉排序的使用方法。

---

## ✅ 範例輸入

輸入: [5, 3, 8, 1, 2]
輸出: [1, 2, 3, 5, 8]


---

## 🧠 解法解析

這裡使用 C++ 的 `vector<int>` 來表示動態陣列，並使用標準函式庫中的 `sort()` 進行排序。

### 🔹 語法說明

- `vector<int> nums = {...}`：宣告並初始化動態陣列
- `sort(nums.begin(), nums.end())`：將整個陣列排序（由小到大）
- `for (int num : nums)`：使用 range-based for 迴圈輸出每個元素

---

## 💡 C++ 程式碼

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main() {
    vector<int> nums = {5, 3, 8, 1, 2};
    
    // 進行排序
    sort(nums.begin(), nums.end());

    // 輸出結果
    for (int num = 0; num < nums.size(); num++)) {
        cout << num << " ";
    }

    return 0;
}
