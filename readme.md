# 1141 德文法學課程筆記 (NTU German Jurisprudence Notes)

國立臺灣大學 1141 德文法學課程的筆記、導讀以及延伸資料，搭配德文原文與法律德文語料整理，協助同學與研究者快速掌握民法與基本權的交會脈絡。專案同時提供 MkDocs 靜態網站與 Jupyter Notebook 支援，適合課前預習、課後複習與長期存檔。

## 快速連結
- 線上筆記網站：<https://mt019.github.io/1141_German_Jurisprudence/>
- MkDocs 設定檔：`mkdocs/mkdocs.yml`
- 課程筆記根目錄：`mkdocs/My_Notes/`

## 專案特色
- 依課程進度整理的逐週導讀與 Rn. 分析，保留老師與同學互動筆記。
- 德文原文搭配語彙標註、使用情境與中文備註，方便跨語對照。
- 收錄課堂推薦的期刊、資料庫與延伸閱讀，打造德文法學資料索引。
- 啟用 MkDocs Material 題材與 SEO 外掛（minify、RSS、git revision date），改善搜尋曝光與閱讀體驗。

## 系統需求
- Docker 與 Docker Compose v2
- （可選）Python 3.10 以上與 `pip`，供不透過容器時使用

## 使用 Docker 預覽
1. 啟動 MkDocs 頁面服務：
   ```bash
   docker compose up docs
   ```
   完成後可在 <http://127.0.0.1:11417/> 預覽網站內容，修改 Markdown 會立即熱更新。
2. 啟動 Jupyter Lab 方便撰寫或檢視 Notebook：
   ```bash
   docker compose up jupyter
   ```
   預設暴露於 <http://127.0.0.1:11418/>，已關閉 Token 與密碼驗證，僅限本機使用。
3. 需要同時啟動兩個服務時，可一次執行：
   ```bash
   docker compose up docs jupyter
   ```

## 手動環境（可選）
若想在本機直接安裝套件，可參考以下步驟：
1. 建立並啟用虛擬環境：
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```
2. 安裝必要套件：
   ```bash
   pip install -r requirements.txt
   ```
3. 啟動 MkDocs 開發伺服器：
   ```bash
   mkdocs serve -f mkdocs/mkdocs.yml
   ```
   預設於 <http://127.0.0.1:8000/> 可即時預覽。
4. 若需啟動教學用 Jupyter Lab，可執行：
   ```bash
   bash scripts/jupyter_url.sh
   ```

## 資料夾結構概要
```text
1141_German_Jurisprudence/
├─ mkdocs/
│  ├─ mkdocs.yml          # MkDocs 主設定檔，含 SEO 與主題設定
│  ├─ My_Notes/           # 課程筆記、名詞整理、額外資源
│  │  ├─ index.md         # 首頁導覽與最新課程紀錄
│  │  └─ Auer/, 小知識/   # 分主題筆記
│  └─ My_Notes/assets/    # 客製化 CSS、JS、Mermaid、MathJax 設定
├─ notebooks/             # 補充 Jupyter Notebook 資料
├─ scripts/               # 工具腳本（例如 jupyter_url.sh）
├─ requirements.txt       # MkDocs 與相關外掛相依性
└─ readme.md              # 專案說明（本檔案）
```

## SEO 與內容維護建議
- 全站描述、作者資訊與社群連結統一於 `mkdocs/mkdocs.yml` 管理，調整後建議重新部署。
- 透過 Markdown 前置欄位 (`keywords`, `description`) 為重要頁面設定中英關鍵字，以利 RSS 與搜尋引擎擷取。
- 新增頁面時，可參考 `My_Notes/index.md` 的範例結構，保留導覽層級與語彙標註格式。
- 若需要額外的 SEO 標籤，可在 `mkdocs/My_Notes/overrides/` 內新增對應模板。

## 發佈與部署
- Docker 模式：
  ```bash
  docker compose run --rm docs build -f mkdocs/mkdocs.yml
  ```
  產生的靜態檔案位於 `site/` 目錄，可直接部署或搭配 CI/CD。
- GitHub Pages：
  ```bash
  mkdocs gh-deploy --clean -f mkdocs/mkdocs.yml
  ```
- 其他靜態網站伺服器：
  ```bash
  mkdocs build -f mkdocs/mkdocs.yml
  ```
  產生的靜態檔案同樣位於 `site/` 目錄，可上傳至任何支援靜態檔案的主機。

## 貢獻方式
1. Fork 或建立新分支。
2. 新增或更新筆記前，請確認原文出處、引註與版權資訊。
3. 送出 Pull Request 時簡述主要更動與參考資料，方便審閱。

—

持續更新中，歡迎同學與研究夥伴共同補充德文法學資料與閱讀心得。
