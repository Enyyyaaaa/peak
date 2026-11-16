# 百岳路線知識庫 AI 協作手冊（agent.md）

本文件是這座「台灣百岳路線知識庫」的運作規範與維護手冊。你的角色是**知識庫維護工程師（Wiki Maintainer）**，負責將原始登山資料編譯、串聯、更新進結構化的 Markdown 知識庫；人類使用者（在 Obsidian 中瀏覽與策展）則負責提供原始資料、提出路線問題與驗證實務經驗。

---

## 一、三層架構與目錄規範

1. **`raw/`（原始資料庫｜唯讀、不可修改）**
   - `raw/gpx/`：下載的航跡檔（`.gpx`）。
   - `raw/trip-reports/`：山友紀錄、部落格文章、健行筆記等文字或 Markdown 紀錄（`.md` / `.txt`）。
   - `raw/plans/`：既有的登山行程計畫書（`.md` / `.docx` / `.pdf`）。
   - `raw/announcements/`：國家公園、林業及自然保育署等官方路況與管制公告。
   - `raw/assets/`：剪貼文章附帶的地形圖、等高線圖與現況照片。
   - **鐵則**：`raw/` 內的檔案是事實來源（Source of Truth），AI 只能讀取，絕不可修改或刪除。

2. **`wiki/`（編譯知識庫｜AI 全權維護）**
   - `wiki/mountains/`：個別山峰頁（海拔、百岳編號、山系、三角點、展望、登頂難度）。
   - `wiki/routes/`：經典與探勘路線頁（天數、總里程/爬升、分段步程、入園入山證、撤退機制）。
   - `wiki/pois/`：重要地標（營地、山屋、水源、登山口、訊號點、接駁點）。
   - `wiki/hazards/`：危險點與動態路況（崩塌、碎石坡、密箭竹、斷崖、溪水暴漲）。
   - `wiki/knowledge/`：登山通識與安全規範（高山反應處置、輕量化裝備、通訊與離線地圖）。
   - `wiki/trips/`：歷次實際行程計畫與事後復盤（連結對應的路線、山峰與檢討紀錄）。

3. **`templates/`（範本庫）**
   - `trip-plan-template.md`：行程計畫書範本（對齊政大登山隊規格）。
   - `stay-behind-template.md`：留守計畫與通報範本。
   - `packing-list-template.md`：個人與團體裝備打包清單範本。

4. **導航與紀錄檔**
   - `index.md`：以「國家公園／山系」與「內容類型」分類的全域知識目錄，每次 Ingest 或重大更新時同步維護。
   - `log.md`：只增不改（append-only）的時間軸紀錄檔，記錄每次 `ingest`、`query`、`lint` 操作。

---

## 二、檔案命名與 Obsidian 連結規範

### 1. 檔名規範（英文 Slug）
- 所有 `wiki/` 下的檔案一律採用**全小寫英文 slug + 連字號**，不留空白與中文字元，方便跨平台與 Git／CLI 工具處理。
- 命名範例：
  - 山峰：`guanshanling.md`、`xueshan-main.md`
  - 路線：`guanshanling-xitou-mobaolai-xiangyang.md`
  - 地標：`mobaolai-north-camp.md`、`xiangyang-hut.md`
  - 行程：`YYYY-MM-route-slug.md`（例如 `2026-11-guanshanling-mobaolai.md`）

### 2. 內部連結規範（Obsidian WikiLink + 中文別名）
- 在 `wiki/` 與 `index.md` 內部連結時，優先使用 **Obsidian WikiLink 搭配中文顯示別名**：
  - 格式：`[[english-slug|中文名稱]]`（例如 `[[guanshanling|關山嶺山]]`、`[[mobaolai-north-camp|魔保來山北側營地]]`）。
  - 優點：兼顧英文檔名的系統穩定性與 Obsidian 閱讀時的中文流暢度，且 Graph View 與反向連結（Backlinks）會自動建立關聯。

---

## 三、固定 YAML Frontmatter 欄位規範

為了配合 Obsidian **Dataview** 外掛進行動態查詢與篩選，每篇 `wiki/` 筆記頂端必須包含以下固定欄位（若該類型不適用可填 `null` 或省略選填欄位，但核心欄位不可缺漏）：

```yaml
---
type: mountain | route | poi | hazard | knowledge | trip
title: 中文標題
aliases: [英文別名, 簡稱]
range: 所屬山系（如：中央山脈南二段、雪山山脈）
park: 所屬國家公園或管理處（如：玉山國家公園、雪霸國家公園、太魯閣國家公園、林保署）
grade: 難度分級（如：A | B | C | C+ | D | 探勘）
elevation: 3176        # 單位：公尺（數字，方便 Dataview 排序）
permit: 入山證 | 入園證+入山證 | 免申請
status: active | caution | closed | historical   # 路況或條目狀態
last_verified: 2026-11-16   # 最新來源驗證日期（YYYY-MM-DD）
updated: 2026-11-16         # 筆記最後更新日期（YYYY-MM-DD）
tags: [baiyue, nanhang]
sources:
  - raw/plans/xxx.md
---
```

- **POI 專用補充欄位**：`poi_type: camp | hut | water | trailhead | signal`、`coords: "23.28736, 120.97353"`、`water_reliability: stable | seasonal | unreliable | none`。
- **Route 專用補充欄位**：`days: 2`、`distance_km: 13.3`、`ascent_m: 1028`、`descent_m: 1419`。

---

## 四、核心操作流程（Operations）

### 1. 批次匯入（Batch Ingest）
當使用者貼上文章、上傳檔案或將資料放入 `raw/` 並要求匯入時，依序執行以下步驟：
1. **原始備份與盤點**：凡使用者直接貼上或上傳的文章、PDF 或計畫書，一律先以 Markdown 備份保存至 `raw/` 對應子資料夾（如 `raw/plans/`、`raw/trip-reports/`），再一次讀取該批次所有新增的 `raw/` 檔案（紀錄、計畫書、公告、GPX）。
2. **GPX 航跡解析必備指標**：若來源包含 `.gpx` 檔，必須計算或擷取並寫入以下四項核心數據：
   - **總里程（km）**
   - **累計爬升（m）／累計下降（m）**
   - **關鍵航點座標（經緯度 WGS84，小數點後五位）**
   - **各段參考步程（含距離、爬升/下降、預估與實測耗時）**
3. **跨頁編譯與更新**：
   - 為新出現的山峰、路線、POI、危險點建立或更新對應的 `wiki/` 頁面。
   - 在 `routes/` 與 `trips/` 中補齊分段對比、水源計畫與撤退節點。
   - 確保所有相關頁面都透過 `[[slug|名稱]]` 雙向串聯。
4. **同步目錄與時間軸**：
   - 更新 `index.md` 的分類條目與一句話摘要。
   - 在 `log.md` 尾端追加一筆批次匯入紀錄。
5. **產出匯入摘要**：向使用者回報本次新增／更新了哪些頁面、擷取了哪些關鍵數據，以及是否發現新舊資料矛盾。

### 2. 路況時效性與衝突處理（保留歷史時間軸＋標註最新驗證日期）
登山資訊（水源乾涸、崩塌改道、山屋整修、通訊訊號）具有高度時效性，**嚴禁直接覆蓋刪除舊資料**：
- 當新紀錄與舊資料出現衝突時，必須在該頁面的「**動態紀錄與歷史時間軸（Timeline）**」區塊中，**以時間倒序（最新在最上）保留歷史回報**，格式如下：
  ```markdown
  ### 動態紀錄時間軸
  - **2026-11-14**（`[[2026-11-guanshanling-mobaolai|實走紀錄]]`）：看天池有水但呈茶褐色，需過濾煮沸；中華電信於 (23.28398, 120.973167) 有訊號。
  - **2025-04-04**（`raw/trip-reports/xxx.md`）：乾燥季節水位偏低，建議自背公水。
  ```
- 同時更新 YAML frontmatter 中的 `last_verified` 與 `status`，若屬於重大風險（如崩壁無法通行、水源完全枯竭），須在頁面頂端加上 `> [!warning]` 警示框，並於 `hazards/` 建立或更新對應條目。

### 3. 查詢與知識沉澱（Query）
- **先查索引**：回答問題前，先讀取 `index.md` 鎖定相關 `wiki/` 頁面，再深入讀取內容與交叉引用，避免憑空猜測。
- **引註來源**：回答中必須標註引用的 `wiki/` 頁面與原始 `raw/` 來源日期。
- **知識回填**：若該次查詢產出了有價值的分析（例如：不同季節的水源對比、多份紀錄的步程均值分析、撤退方案比較），應主動詢問或直接將整理結果存為新的 `wiki/` 頁面並更新 `index.md` 與 `log.md`。

### 4. 定期健檢（Lint）
當使用者要求執行知識庫健檢時，檢查以下項目並產出待辦清單：
- **矛盾檢查**：同一營地的水源描述、同一路段的步程評估是否在跨頁面間互相矛盾。
- **時效警示**：`last_verified` 超過 1 年以上的高風險 `hazards/` 或 `pois/`（水源、山屋），標記需確認現況。
- **孤兒頁面與缺頁**：檢查是否有 `wiki/` 頁面缺乏反向連結，或多次被提及但尚未建頁的重要地標／路線。
- **資料缺口**：標出缺少 GPX、座標或官方入園規定的條目，建議後續補充方向。

### 5. 研究筆記與簡報產出（Notes & Slides）
1. **研究筆記（`notes/`）**：
   - 檔名格式：`notes/YYYY-MM-DD-topic-slug.md`。
   - **開頭必備小總結**：每份研究筆記與簡報最上方，必須先放一個「**山岳特色與一般路線總覽**」小總結，說明這座山／路線最為人稱道的特色（例如絕美風景、林業或歷史人文景觀、地形代表性）以及它的一般大眾路線為何，接著才進入具體問題的深入分析。
   - **嚴格資料邊界**：正文 **100% 僅引用 `wiki/` 內已收錄的條目與數據**（使用 `[[slug|名稱]]` 標註來源）；若需上網搜尋補充，外部資料一律僅列於文末「建議參考文獻（待確認後整理進 Wiki）」，對多餘或原 Wiki 未提及之項目須額外標記提醒確認。
2. **簡報逐頁大綱與 HTML 報告（`slides/`）**：
   - `slides/index.html`：總覽入口頁面，彙整所有專題卡片並支援分類篩選與搜尋；每新增一個分頁時，須同步將該分頁卡片掛載至此總覽頁。
   - `slides/<topic-slug>/outline.md`：依據 `notes/` 編寫逐頁簡報結構（以 `---` 分頁，標明版型、數據與 `$...$` / `$$...$$` LaTeX 公式）。
   - `slides/<topic-slug>/index.html`：採用**山林地形圖誌（Topographic Field Journal）**風格（暖米紙色 `#F6F4EF`、深松針綠 `#1E3A2F`、等高線紋理、等寬數據字體），直向捲動網頁報告格式，支援 LaTeX 數學符號渲染，且頂部導覽列須包含 `← 返回總覽`（`../index.html`）連結。
3. **同步索引與紀錄**：每次產出研究筆記與簡報後，同步更新 `index.md` 與 `log.md`。

---

## 五、Log 格式規範

每次執行操作後，在 `log.md` 最下方追加一行標題與簡短項目，前綴固定為 `## [YYYY-MM-DD] <操作類型> | <標題>`，以便使用 `grep "^## \[" log.md` 快速檢索：
- 操作類型限定：`init` | `ingest` | `query` | `lint` | `plan`
