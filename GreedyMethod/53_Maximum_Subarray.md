# 53\_Maximum\_Subarray

## 題目描述

給定一個整數陣列 `nums`，找出一個具有最大總和的連續子陣列（子陣列最少包含一個元素），並回傳其總和。

---

## 範例

### Example 1:

```
輸入: nums = [-2,1,-3,4,-1,2,1,-5,4]
輸出: 6
解釋: 連續子陣列 [4,-1,2,1] 的總和最大，為 6。
```

### Example 2:

```
輸入: nums = [1]
輸出: 1
```

### Example 3:

```
輸入: nums = [5,4,-1,7,8]
輸出: 23
```

---

## 解題想法


定義：

* `curSum`：當前子陣列的總和（包含 nums\[i]）
* `maxSum`：目前遇到的最大總和

每一步：

* `curSum = max(nums[i], curSum + nums[i])`

  * 代表要「重新開始子陣列」或「繼續累加」
* 更新最大總和 `maxSum = max(maxSum, curSum)`

---

## C++ 程式碼

```cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int maxSum = nums[0];
        int curSum = nums[0];
        for (int i = 1; i < nums.size(); ++i) {
            curSum = max(nums[i], curSum + nums[i]);
            maxSum = max(maxSum, curSum);
        }
        return maxSum;
    }
};
```