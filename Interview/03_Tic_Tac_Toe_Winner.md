# LeetCode 練習：03_Tic_Tac_Toe_Winner（判斷圈圈叉叉勝負）

## 📝 題目說明

你正在玩一個井字棋（Tic Tac Toe）遊戲，有兩位玩家：
- 玩家 A 使用 `X`
- 玩家 B 使用 `O`

給定一組玩家依序下的棋步（moves），請判斷比賽結果：
- 若有一方獲勝，回傳 `"A"` 或 `"B"`
- 若還沒分出勝負且格子已滿，回傳 `"Draw"`
- 若還沒分出勝負且還沒填滿，回傳 `"Pending"`

---

## ✅ 範例輸入

```
輸入: moves = [[0,0],[2,0],[1,1],[2,1],[2,2]]
輸出: "A"
說明: 玩家 A 形成了一條對角線
```

---

## 🧠 解法解析

1. 建立一個 3x3 的棋盤 `board`，初始為空白字元 `' '`。
2. 玩家 A 與 B 依序下棋，奇數步是 A，偶數步是 B。
3. 每下一步就更新棋盤內容。
4. 最後檢查所有橫線、直線、兩條對角線是否有三個相同的符號。

---

## 💡 C++ 程式碼

```cpp
#include <iostream>
#include <vector>
#include <string>

using namespace std;

string tictactoe(vector<vector<int>>& moves) {
    // 建立 3x3 棋盤並初始化為空白
    vector<vector<char>> board(3, vector<char>(3, ' '));

    for (int i = 0; i < moves.size(); ++i) {
        int r = moves[i][0];
        int c = moves[i][1];
        
        if (i % 2 == 0) {
            board[r][c] = 'X'; // A 的回合
        } 
        else {
        board[r][c] = 'O'; // B 的回合
        }
    }

    // 檢查橫線與直線
    for (int i = 0; i < 3; i++) {
        if (board[i][0] != ' ' && board[i][0] == board[i][1] && board[i][1] == board[i][2])
            {
            if (board[i][0] == 'X') return "A";
            else return "B";
            }
        if (board[0][i] != ' ' && board[0][i] == board[1][i] && board[1][i] == board[2][i])
            {
            if (board[0][i] == 'X') return "A";
            else return "B";
            }
    }

    // 檢查對角線
    if (board[0][0] != ' ' && board[0][0] == board[1][1] && board[1][1] == board[2][2])
        {
        if (board[0][0] == 'X') return "A";
        else return "B";
        }
    if (board[0][2] != ' ' && board[0][2] == board[1][1] && board[1][1] == board[2][0])
        {
        if (board[0][2] == 'X') return "A";
        else return "B";
        }

    // 判斷未完或平手
    if (moves.size() == 9)
        return "Draw";
    else
        return "Pending";
}
```

---

## 🔍 程式碼說明

- `vector<vector<char>> board(3, vector<char>(3, ' '))`：建立 3x3 棋盤並初始化為空白字元。
- `i % 2 == 0`：判斷目前是第幾步，偶數代表玩家 A。
- 每走一步就更新該位置上的棋子，之後檢查是否有連線。

---

## 📌 小結

| 狀況 | 回傳值 |
|------|--------|
| 玩家 A 獲勝 | `"A"` |
| 玩家 B 獲勝 | `"B"` |
| 所有格子填滿無勝負 | `"Draw"` |
| 尚未填滿也未分出勝負 | `"Pending"` |