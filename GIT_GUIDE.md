
# Git & GitHub 操作小抄（GIT_GUIDE）

這是我的 Git & GitHub 基本操作筆記，記錄從本地端開發到同步到 GitHub 的完整流程，適合管理 LeetCode 題解、專案版本控制等。

---

## 🧾 一、Git 使用者初始設定（只需一次）

```bash
git config --global user.name "你的 GitHub 使用者名稱"
git config --global user.email "你的 GitHub 註冊 Email"
```

---

## 📦 二、Clone GitHub 專案到本地端

```bash
git clone https://github.com/你的帳號/你的專案名稱.git
```

範例：

```bash
git clone https://github.com/av121036/leetcode-cpp.git
```

---

## 📂 三、處理檔案（新增、移動）

```bash
mkdir 資料夾名稱                  # 建立資料夾
move 檔案名稱 資料夾/             # 移動檔案到資料夾（Windows）
```

---

## 🔍 四、查看目前變更狀態

```bash
git status
```

---

## ✅ 五、加入變更檔案（暫存）

```bash
git add 檔案名稱                 # 加入指定檔案
git add .                       # 加入所有變更的檔案
```

---

## 📝 六、提交變更（建立版本）

```bash
git commit -m "這次修改的簡短描述"
```

---

## 🚀 七、上傳到 GitHub（推送）

```bash
git push origin main
```

如果你在其他分支上，例如 `dev`：

```bash
git push origin dev
```

---

## 🧠 八、其他常用指令

```bash
git log                 # 查看歷史提交紀錄
git rm 檔案名稱         # 從版本控制中移除檔案
git branch              # 查看目前所在分支
git checkout -b 新分支名稱  # 建立並切換到新分支
```

---

## 📁 專案資料夾建議結構（LeetCode 題解範例）

```
leetcode-cpp/
├── StackAndQueue/
│   └── 20_Valid_Parentheses.md
├── Array/
│   └── 1_Two_Sum.md
├── README.md
└── GIT_GUIDE.md
```

---

## 🧷 README 連結範例

```markdown
## Stack and Queue
- [20. Valid Parentheses](./StackAndQueue/20_Valid_Parentheses.md)

## Array
- [1. Two Sum](./Array/1_Two_Sum.md)
```

---

📌 歡迎依照自己的專案類型與習慣擴充這份小抄，養成良好的版本控制與解題紀錄習慣 💪
