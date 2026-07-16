# 🎓 AI 數位與紙本考卷產生器 (有聲簡報版)

這是一個專門為教師設計的 AI 考卷與有聲簡報生成技能 (Skill)。

使用者只需將此 GitHub 儲存庫網址提供給 AI 助理，並說 **「安裝這個 Skill」**，AI 即可自動配置並載入此出題技能，引導您一鍵生成符合特教點讀與教師講解簡報需求的六合一教學媒材！

---

## 🛠️ 安裝與使用方式（極簡步驟）

### 步驟一：安裝 Skill
直接在 AI 助理的對話框中輸入：
> **「幫我安裝這個 Skill： https://github.com/chuoneone/exam_generator 」**

AI 助理會自動將此倉庫 Clone 到本機的 Skill Customizations 目錄並載入。

### 步驟二：貼上主題或網址，開始出題
安裝完成後，直接對 AI 助理說出您想出的題目範圍，並貼上教材或網址，例如：
* *「幫我根據這個單元出一份物理考卷：高一牛頓第二運動定律，共 10 題」*
* *「幫我依據《視力與偏見》課文，出 20 題練習卷與解析卷，字體要 14pt」*

AI 助理將會啟動**互動式選擇題問答**（使用 `ask_question` 系統工具），與您確認題型、配分、字型大小及答案解析需求，隨後在您的工作區中自動產出六合一檔案。

---

## ✨ 核心特色

### 🗂️ 六合一檔案同步輸出
每次出題皆會於同一個資料夾中同步生成以下六種格式：

1. **學生用點讀有聲 HTML** (`_學生點讀.html`)：支援句子分段點讀與語速調整，適合自主學習或特教報讀。
2. **教師用講解簡報 HTML** (`_教師簡報.html`)：全螢幕投影片版面，包含手寫電子白板與整題 TTS 朗讀，且答案解析預設隱藏。
3. **學生用練習卷 PDF** (`_練習卷.pdf`)：乾淨的 A4 PDF 考卷，**自動去除頁首頁尾瀏覽器檔案網址與日期**。
4. **學生用練習卷 Word** (`_練習卷.docx`)：原生 Word 格式，便於教師手動調整排版。
5. **教師用解析卷 PDF** (`_解析.pdf`)：包含紅色答案與詳細解析的 PDF 文件。
6. **教師用解析卷 Word** (`_解析.docx`)：包含完整解析之 Word 電子檔。

### 📐 跨學科與公式渲染支援
* **不限學制與學科**：全面支援國小、國中、高中至大專院校的國文、英文、數學、理化、社會科學、程式設計等各種科目。
* **數學公式（KaTeX & OMML）**：HTML 算式採用 LaTeX 編碼並由 **KaTeX** 進行印刷級美化渲染；Word 中的數學公式自動轉換為原生可編輯的 **Office Math (OMML)** 結構，不顯現原始 raw LaTeX 程式碼。

### 🎨 HTML 固定模板自訂
本專案採用**固定模板機制**，所有的 HTML 輸出皆依據 `templates/` 下的模板渲染，讓每次產出的網頁風格與邏輯始終一致：
- [student_template.html](skills/paper_exam_generator/resources/templates/student_template.html) (學生點讀模板)
- [teacher_template.html](skills/paper_exam_generator/resources/templates/teacher_template.html) (教師簡報模板)

---

## 📁 儲存庫結構

```text
exam_generator/
├── README.md                        # 本說明文件
├── generate_quiz.py                 # 核心考卷生成 Python 腳本（相對路徑版）
└── skills/
    └── paper_exam_generator/
        ├── SKILL.md                 # AI 技能指令與規範說明檔（核心）
        └── resources/
            └── templates/           # 考卷網頁與簡報的固定模板
                ├── student_template.html
                └── teacher_template.html
```
