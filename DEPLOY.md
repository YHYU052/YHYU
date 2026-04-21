# TECH SQUIDS 個人網頁 — 部署說明

## 📁 檔案結構

部署前，請在同一資料夾內建立以下結構：

```
你的專案資料夾/
├── index.html          ← 主網頁（已提供）
├── assets/
│   └── logo.png        ← 放入你的 TECH SQUIDS Logo 圖
└── handouts/
    ├── ai-2024.pdf
    ├── tui-2024.pdf
    ├── pbl-2023.pdf
    ├── n8n-2025.pdf
    ├── rag-2025.pdf
    └── esp32-2023.pdf
```

---

## 🚀 GitHub Pages 部署步驟

### Step 1：建立 GitHub Repository

1. 前往 https://github.com → 右上角「+」→「New repository」
2. Repository name 填：`yhyu-workshop`（或你喜歡的名稱）
3. 設為 **Public**（GitHub Pages 免費版需要 Public）
4. 按「Create repository」

### Step 2：上傳檔案

**方法 A：網頁直接上傳（簡單）**

1. 進入你的 repository 頁面
2. 點「Add file」→「Upload files」
3. 拖拉所有檔案（index.html、assets 資料夾、handouts 資料夾）上去
4. 按「Commit changes」

**方法 B：使用 Git 指令（進階）**

```bash
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/你的帳號/yhyu-workshop.git
git push -u origin main
```

### Step 3：開啟 GitHub Pages

1. 進入 repository → 上方「Settings」
2. 左側選單找「Pages」
3. Source 選「Deploy from a branch」
4. Branch 選「main」，資料夾選「/ (root)」
5. 按「Save」

稍等 1-2 分鐘後，網址會顯示在：
```
https://你的GitHub帳號.github.io/yhyu-workshop/
```

---

## ✏️ 客製化說明

### 修改個人資訊
開啟 `index.html`，搜尋以下關鍵字並替換：

| 搜尋內容 | 說明 |
|---------|------|
| `新北市柑園國中` | 修改為你的學校 |
| `f1991714@gmail.com` | 修改為你的信箱 |
| `YHYU` | 修改為你的名字 |
| `countWorkshops`, `countWorks`, `countYears` | 修改數字（在 JS 段落） |

### 修改講義密碼

在 `index.html` 底部 `<script>` 區塊找到 `HANDOUTS` 陣列：

```javascript
const HANDOUTS = [
  {
    id: 'ai2024',
    title: '生成式 AI 融入教學設計實戰班',
    password: 'TSAI2024',     // ← 改這裡
    url: 'handouts/ai-2024.pdf'  // ← 確認檔案名稱
  },
  // ...
];
```

每份講義可設定不同密碼。

### 新增講義卡片

在 `HANDOUTS` 陣列中加入新物件：

```javascript
{
  id: 'new2026',
  title: '你的工作坊名稱',
  date: '2026 / 09',
  format: 'PDF',
  size: '2.0 MB',
  desc: '講義內容說明',
  tags: ['標籤1', '標籤2'],
  icon: 'fa-star',           // Font Awesome 圖示名稱
  password: '你的密碼',
  url: 'handouts/new-2026.pdf'
},
```

### 新增作品展示卡片

在 `<!-- 以下為範例卡片 -->` 區塊後複製一個 `.work-card` div，修改內容即可。

### 新增預告場次

在 `<div class="timeline" id="timeline">` 內複製一個 `.timeline-item` 並修改內容。

---

## 🎨 配色說明

網頁使用 CSS 變數，可在 `:root` 區塊統一調整：

```css
:root {
  --red:       #CC2222;   /* 主色（紅） */
  --red-bright:#FF3333;   /* 高亮紅 */
  --black:     #060606;   /* 背景黑 */
  --card:      #0e0e0e;   /* 卡片背景 */
  --white:     #f0f0f0;   /* 文字白 */
}
```

---

## ❓ 常見問題

**Q：Logo 不顯示？**
A：確認 `assets/logo.png` 路徑正確，檔名要完全相符（含大小寫）。

**Q：講義下載後顯示 404？**
A：確認 `handouts/` 資料夾已上傳到 GitHub，且檔名與 `url` 設定相符。

**Q：想加上 Google Analytics？**
A：在 `</head>` 前插入 GA 追蹤碼即可。

**Q：密碼可以改成更安全的方式嗎？**
A：目前為 client-side 驗證，適合研習講義防護。如需更高安全性，可搭配 Netlify Functions 或 Firebase 做後端驗證。

---

*TECH SQUIDS × YHYU — 柑園國中 2026*
