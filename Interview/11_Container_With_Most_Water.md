# 11\_Container\_With\_Most\_Water

## ⭐ 題目描述 (Container With Most Water)

給一個正整數列表 `height` ，其中每個元素代表一條垂直線的高度，請找出兩條線可與 x 軸建成最大儲水容器。

### 範例

```text
輸入: height = [1,8,6,2,5,4,8,3,7]
輸出: 49
解釋: 在第 2 條 (高 8) 和第 9 條 (高 7)之間的距離為 7，最大儲水量 = min(8, 7) * 7 = 49
```

---

## 🧰 解題思路: 雙指針法 (Two Pointers)

1. 設定兩個指針在陣列兩端：`left = 0`，`right = n - 1`
2. 每次計算兩條線的儲水量: `min(height[left], height[right]) * (right - left)`
3. 記錄最大值
4. 移動較短的那條線：因為距離縮短，想讓高度增加來擴大儲水量

---

## ✅ C++ 解法

```cpp
#include <vector>
#include <algorithm>
using namespace std;

int maxArea(vector<int>& height) {
    int left = 0, right = height.size() - 1;
    int maxArea = 0;

    while (left < right) {
        int h = min(height[left], height[right]);
        int w = right - left;
        maxArea = max(maxArea, h * w);

        // 移動較短的線
        if (height[left] < height[right]) {
            ++left; // 或用 left++ 效果相同
        } else {
            --right;
        }
    }

    return maxArea;
}
```

---

## ⏱ 複雜度分析

| 類型 | 複雜度  |
| -- | ---- |
| 時間 | O(n) |
| 空間 | O(1) |

---