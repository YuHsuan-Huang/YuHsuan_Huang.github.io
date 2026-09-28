# 黃聿瑄個人作品集｜修改與上傳說明

公開網站：<https://yuhsuan-huang.github.io/>

這份網站使用單一入口檔案 `index.html`。文字、版面與作品資料大多都寫在這個檔案中。

> 重要：目前請以根目錄的 `index.html` 為準。`direct-upload.html`、`dist/` 和舊的 `EDITING_GUIDE.md` 都不是 GitHub Pages 現在發布的版本，請不要再修改或上傳它們。

## 一、資料夾應有的結構

```text
portfolio-site/
├─ index.html             網站主程式，GitHub 一定要放在最外層
├─ README.md              這份修改說明
├─ photos/                所有封面、證書與圖片
│  ├─ project-01.jpg
│  ├─ project-03.jpg
│  ├─ project-07.jpg
│  ├─ toeic.jpg
│  └─ ...
└─ files/                 所有報告、簡報與成績單 PDF
   ├─ HCI.pdf
   ├─ database1.pdf
   ├─ database_ppt.pdf
   ├─ transcript.pdf
   └─ ...
```

GitHub 最外層只需要保留：

```text
index.html
README.md
photos/
files/
```

不要把照片或 PDF 重複放在 GitHub 最外層，也不要上傳 `.openai/`、`.sites-runtime/`、`dist/`、`videos/`。

## 二、修改前的固定流程

1. 使用 VS Code 開啟根目錄的 `index.html`。
2. 用 `Ctrl + F` 搜尋本說明提供的關鍵字。
3. 修改後按 `Ctrl + S` 儲存。
4. 雙擊 `index.html`，用瀏覽器確認畫面與連結。
5. 確認正常後，再更新 GitHub 上的 `index.html`。

不要同時修改 `direct-upload.html` 和 `index.html`，否則容易不知道哪一份才是最新版。

## 三、快速對照表

| 想修改的內容 | 在 `index.html` 搜尋 | 檔案放置位置 |
|---|---|---|
| 姓名、首頁大標題 | `★★★★★ 網站內容修改區 ★★★★★` | 不需另外上傳檔案 |
| 關於我 | `aboutTitle:` | 不需另外上傳檔案 |
| 作品卡與作品內頁 | `projects: [` | 圖片放 `photos/`，PDF 放 `files/` |
| 作品封面 | `photo:"photos/` | `photos/檔名.jpg` |
| YouTube Prototype | `youtubeId:` | 不需上傳影片 |
| 作品報告或簡報 | `links:[` | `files/檔名.pdf` |
| 研究計畫 | `id="research-plan"` | 不需另外上傳檔案 |
| 讀書計畫 | `id="study-plan"` | 不需另外上傳檔案 |
| 證書卡片 | `id="certificates"` | 圖片放 `photos/` |
| 成績與修課紀錄 | `id="courses"` | 成績單放 `files/transcript.pdf` |
| 實務工作經驗 | `id="experience"` | 不需另外上傳檔案 |
| 導覽列 | `<ul class="nav-links">` | 不需另外上傳檔案 |
| 黑白灰配色 | `最終黑白灰配色` | 不需另外上傳檔案 |

## 四、修改首頁文字與關於我

在 `index.html` 搜尋：

```text
★★★★★ 網站內容修改區 ★★★★★
```

下面的 `CONTENT` 是主要文字修改區：

```javascript
const CONTENT = {
  name: "黃聿瑄",
  initials: "YN",
  heroLabel: "PERSONAL PORTFOLIO · 2026",
  heroTitle: "首頁大標題",
  heroSubtitle: "個人申請作品集",
  heroDescription: "首頁簡短說明",
  aboutTitle: "我是芋頭。",
  aboutLead: "關於我的重點介紹。",
  aboutText: [
    "第一段關於我。",
    "第二段關於我。"
  ],
  tags: ["研究分析", "內容企劃", "團隊合作", "實作能力"],
```

只修改引號內的文字。逗號、引號、中括號和大括號要保留。

## 五、修改一張作品卡

在 `CONTENT` 裡搜尋：

```javascript
projects: [
```

每一組 `{ ... }` 就是一件作品：

```javascript
{
  number:"03",
  category:"資訊系統",
  type:"資料庫設計專案",

  title:"資料庫設計專案",
  summary:"顯示在作品卡上的簡短說明。",

  photo:"photos/project-03.jpg",
  photoAlt:"動漫目錄資料庫系統畫面",

  links:[
    {
      label:"查看書面報告",
      url:"files/database1.pdf"
    },
    {
      label:"查看成果簡報",
      url:"files/database_ppt.pdf"
    }
  ],

  year:"2025",
  role:"需求分析／資料庫設計／成果製作",
  duration:"4 週",
  overview:"專案背景。",
  process:"執行過程。",
  outcome:"成果與反思。"
},
```

欄位用途：

- `number`：作品編號，不能重複。
- `category`：卡片上顯示的分類。
- `type`：作品形式。
- `title`：作品名稱。
- `summary`：卡片摘要。
- `photo`：封面圖片路徑。
- `photoAlt`：圖片的文字說明。
- `links`：點進作品後的報告、簡報或外部連結按鈕。
- `year`、`role`、`duration`：專案基本資料。
- `overview`、`process`、`outcome`：作品內頁文字。

## 六、新增一張作品卡

1. 在 `projects: [` 內複製一整組作品資料，從 `{` 複製到對應的 `},`。
2. 貼在最後一張作品後面。
3. 修改 `number`、標題、內容和路徑。
4. 前一組與下一組之間必須有逗號。
5. 封面放入本機 `photos/`。
6. PDF 放入本機 `files/`。
7. GitHub 也要把相同檔案上傳到相同名稱的資料夾。

如果還沒有封面，可以先使用：

```javascript
photo:"photos/project-10.jpg"
```

之後再把 `project-10.jpg` 上傳到 `photos/`。

## 七、新增、刪除或修改作品連結

一個連結：

```javascript
links:[
  {
    label:"查看書面報告",
    url:"files/report.pdf"
  }
],
```

兩個連結：

```javascript
links:[
  {
    label:"查看書面報告",
    url:"files/report.pdf"
  },
  {
    label:"查看成果簡報",
    url:"files/presentation.pdf"
  }
],
```

如果暫時沒有連結，可以寫：

```javascript
links:[],
```

不要使用 `projects:` 代替 `links:`，否則按鈕不會出現。

## 八、加入 YouTube 影片

YouTube 影片請設為「不公開」，不要設為「私人」。

假設影片網址是：

```text
https://youtu.be/t_GWQR4gUHs
```

影片 ID 是最後面的：

```text
t_GWQR4gUHs
```

在該作品資料中加入：

```javascript
youtubeId:"t_GWQR4gUHs",
```

沒有影片的作品不需要加入 `youtubeId`。YouTube 已負責儲存影片，因此不需要把 MP4 或 `videos/` 上傳到 GitHub。

## 九、照片與證書圖片

### 作品封面

1. 圖片放進本機 `photos/`。
2. 建議使用英文小寫檔名，例如：

```text
project-04.jpg
```

3. 在作品資料填入：

```javascript
photo:"photos/project-04.jpg",
```

### 證書圖片

在 HTML 搜尋：

```html
id="certificates"
```

單張圖片：

```html
data-images="photos/toeic.jpg"
```

多張圖片使用 `|` 分隔，中間不要加空格：

```html
data-images="photos/image-01.jpg|photos/image-02.jpg|photos/image-03.jpg"
```

卡片封面則修改 `<img>` 的 `src`：

```html
src="photos/image-01.jpg"
```

## 十、PDF、報告、簡報與成績單

所有 PDF 都放在：

```text
files/
```

HTML 或 JavaScript 中的路徑必須加上 `files/`：

```javascript
url:"files/report.pdf"
```

成績單固定使用：

```html
href="files/transcript.pdf"
```

建議使用簡短的英文檔名，不要使用括號、`#`、`&` 或問號。例如：

```text
research-method.pdf
psychology-statistics.pdf
bibliography.pdf
```

如果修改了檔名，`index.html` 裡的路徑也要一起修改。

## 十一、研究計畫、讀書計畫、課程與實務經驗

這幾個區塊不在 `CONTENT` 裡，需要直接修改 HTML。

使用 `Ctrl + F` 搜尋：

```text
id="research-plan"   研究計畫
id="study-plan"      讀書計畫
id="courses"         成績與修課紀錄
id="experience"      實務工作經驗
```

只修改標籤中間看得到的文字，不要刪除 `<section>`、`<div>`、`</div>` 或 `</section>`。

新增課程時，複製完整的：

```html
<div class="course-item">
  <span>課程名稱</span>
  <strong>A+</strong>
</div>
```

新增實務經驗時，複製完整的一組：

```html
<div class="experience-item">
  ...
</div>
```

## 十二、導覽列與區塊順序

搜尋：

```html
<ul class="nav-links">
```

每個連結的 `href` 必須對應到區塊的 `id`：

```html
<a href="#research-plan">研究計畫</a>
```

對應：

```html
<section id="research-plan">
```

要改頁面順序時，必須移動完整的 `<section> ... </section>`，不能只移動標題。

## 十三、修改黑白灰配色

在 CSS 搜尋：

```text
最終黑白灰配色
```

目前建議配色：

```css
.theme-black{
  background:#0c0c0d;
  color:#f7f7f5;
}

.theme-gray{
  background:#d6d6d3;
  color:#111112;
}

.theme-white{
  background:#f7f7f5;
  color:#111112;
}
```

不要改成彩色；如要調整，只調整黑、白、灰的深淺。

## 十四、更新 GitHub 公開網站

Repository 名稱應為：

```text
yuhsuan-huang.github.io
```

公開網址：

```text
https://yuhsuan-huang.github.io/
```

### 只修改文字或程式

1. 在 GitHub 點開最外層的 `index.html`。
2. 按鉛筆圖示 `Edit this file`。
3. 修改或貼上新版內容。
4. 按 `Commit changes`。

也可以使用 `Add file` → `Upload files`，上傳新的 `index.html` 覆蓋舊版。

### 新增照片

1. 進入 GitHub 的 `photos/`。
2. 按 `Add file` → `Upload files`。
3. 上傳照片。
4. 按 `Commit changes`。

### 新增 PDF

1. 進入 GitHub 的 `files/`。
2. 按 `Add file` → `Upload files`。
3. 上傳 PDF。
4. 按 `Commit changes`。

更新後到 `Actions` 等待 `github-pages` 出現綠色勾勾，再開啟網站並按 `Ctrl + F5`。

## 十五、常見錯誤

### 公開網站沒有更新

- 確認修改的是 GitHub 最外層的 `index.html`。
- 到 `Actions` 查看最新部署是否為綠色勾勾。
- 等待幾分鐘後按 `Ctrl + F5`。
- 確認開啟的是 <https://yuhsuan-huang.github.io/>，不是舊的雙層網址。

### 圖片不見

- 確認圖片確實位於 GitHub 的 `photos/`。
- 檢查英文大小寫是否完全相同。
- `project-01.jpg` 和 `Project-01.jpg` 在 GitHub 是不同檔案。

### PDF 顯示 404

- 確認 PDF 位於 GitHub 的 `files/`。
- 確認程式使用 `files/檔名.pdf`。
- 檢查檔名、空格、大小寫和副檔名。

### 作品全部消失或按了沒反應

通常是 JavaScript 的引號、逗號或括號被刪掉。檢查剛修改的作品資料：

- 文字前後是否都有引號。
- 每個欄位後是否有逗號。
- `links:[ ... ]` 的中括號是否完整。
- 每件作品的 `{ ... }` 是否完整。

### 作品內頁出現重複按鈕或多餘空白

搜尋：

```html
id="detailLinks"
```

整份 `index.html` 只能有一個 `id="detailLinks"`。

## 十六、公開前隱私檢查

GitHub Pages 和 Public Repository 都是公開的。上傳前請檢查：

- 成績單是否含學號、生日或其他識別資料。
- TOEIC 證明是否含生日、照片或報名資料。
- 證書截圖是否含帳號名稱。
- 研究報告是否含組員不希望公開的姓名或聯絡方式。
- YouTube 不公開影片是否出現個資或未取得公開同意的人像。

不希望公開的資料，請先遮蔽或不要上傳。
