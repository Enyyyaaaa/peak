# 百岳路線知識庫 操作時間軸（Log）

本檔案為只增不改（append-only）的操作紀錄，每筆紀錄皆以 `## [YYYY-MM-DD] <類型> | <標題>` 開頭，便於追蹤知識庫演進。

---

## [2026-11-16] init | 建立知識庫架構、中文 agent.md 與範本庫
- 建立 `agent.md`、`index.md`、`log.md` 與 `raw/`、`wiki/`、`templates/` 完整資料夾結構。
- 參考「11/14-15 關山嶺上溪頭魔保出向陽企劃書」建立 `templates/` 三份標準範本（行程計畫書、留守計畫、打包清單）。
- 寫入「關山嶺上溪頭魔保出向陽」示範知識圖譜（涵蓋 `mountains/`、`routes/`、`pois/`、`hazards/`、`knowledge/`、`trips/` 共 7 篇互相連結的條目）。

## [2026-11-16] ingest | 11/14-15 關山嶺上溪頭魔保出向陽企劃書（PDF）
- 原始檔案保存：`raw/plans/2026-11-14-guanshanling-mobaolai-plan.md`。
- 新增 5 篇 `wiki/` 頁面：`[[xitou-mountain|溪頭山]]`、`[[mobaolai|魔保來山]]`、`[[xitou-hut-ruins|溪頭山山屋遺址]]`、`[[small-camp-pond|小營地＋池子]]`、`[[wilderness-medical-protocol|野地醫療應變計畫]]`。
- 更新 `[[guanshanling-xitou-mobaolai-xiangyang|關山嶺上溪頭魔保出向陽]]` 與 `[[2026-11-guanshanling-mobaolai|2026-11 關山嶺上溪頭魔保出向陽]]`，補齊 GPX 參考連結、5 份歷史紀錄與交叉連結，並同步更新 `index.md`。

## [2026-11-16] query | 關山嶺山的撤退路線研究筆記與簡報產出
- 新增 `notes/2026-11-16-guanshanling-retreat-routes.md`（正文嚴格依據 `wiki/` 編寫，文末附 5 筆外部建議參考文獻與待確認項目）。
- 新增 `slides/guanshanling-retreat-routes/outline.md` 與山林地形圖誌風格之 HTML 直向報告，並更新 `agent.md` 與 `index.md`。

## [2026-11-16] ingest | 補充南橫公路管制、溪頭關山嶺 O 型走法與海拔對照
- 依使用者確認，將 3 項外部文獻資訊寫入 `[[guanshanling|關山嶺山]]` 與 `[[guanshanling-xitou-mobaolai-xiangyang|關山嶺上溪頭魔保出向陽]]`：玉管處梅山口–向陽每週二三四禁行與 17:00 淨空管制、38.6K 溪頭山縱走關山嶺山替代走法，以及維基百科 `3,173.7 m` 海拔對照。
- 建立簡報總覽入口頁 `slides/index.html`（支援分類篩選、搜尋與點擊進入各分頁），並於 `slides/guanshanling-retreat-routes/index.html` 加入返回總覽連結。

## [2026-11-16] ingest & query | 巒安堂上西巒大山計劃書與專題報告
- 原始檔案保存：`raw/plans/2026-11-07-luanantang-xiluan-plan.md`。
- 新增 5 篇 `wiki/` 頁面：`[[xiluandashan|西巒大山]]`、`[[luanantang-xiluandashan|巒安堂上西巒大山]]`、`[[luanantang|巒安堂]]`、`[[shuanglong-helipad|雙龍林道停機坪]]`、`[[2026-11-luanantang-xiluandashan|2026-11 巒安堂上西巒大山]]`。
- 新增研究筆記 `notes/2026-11-16-luanantang-hiking-plan.md`、逐頁大綱 `slides/luanantang-hiking-plan/outline.md` 與 HTML 分頁 `slides/luanantang-hiking-plan/index.html`。
- 同步更新 `slides/index.html` 總覽頁、`index.md` 與 `log.md`。
- 依使用者需求，於 `agent.md` 增訂研究筆記與簡報開頭必備「山岳特色與一般路線總覽」小總結之規範，並回溯補齊兩份既有 `notes/` 與 `slides/` HTML 報告。
