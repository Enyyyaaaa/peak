---
type: note
title: 關山嶺山的撤退路線與決策分析
aliases: [關山嶺撤退分析, Guanshanling Retreat Routes]
range: 中央山脈南段（南橫・向陽稜線）
park: 玉山國家公園／林保署台東分署
status: active
last_verified: 2026-11-16
updated: 2026-11-16
tags: [note, retreat, safety, nanheng]
sources:
  - wiki/mountains/guanshanling.md
  - wiki/mountains/xitou-mountain.md
  - wiki/mountains/mobaolai.md
  - wiki/routes/guanshanling-xitou-mobaolai-xiangyang.md
  - wiki/pois/xitou-hut-ruins.md
  - wiki/pois/small-camp-pond.md
  - wiki/pois/mobaolai-north-camp.md
  - wiki/pois/xiangyang-hut.md
  - wiki/hazards/xitou-mobaolai-bamboo-and-scree.md
  - wiki/trips/2026-11-guanshanling-mobaolai.md
  - wiki/knowledge/ams-protocol.md
  - wiki/knowledge/wilderness-medical-protocol.md
---

# 關山嶺山的撤退路線與決策分析

> **資料邊界聲明**：本筆記正文內容**完全依據目前 `wiki/` 內已收錄的條目**編寫；尚未收錄進知識庫的外部網路資料僅列於文末「建議參考文獻」，待確認後再行匯入。

## 導讀小總結｜山岳特色與一般路線

- **最為人稱道的特色**：[[guanshanling|關山嶺山]]（H3176m，百岳 #58）與庫哈諾辛山、塔關山並稱「**南橫三星**」，以平易近人的距離卻擁有極佳的**開闊稜線展望與雲海**著稱；雖是三星中路程最短的一座，但沿途包含碎石陡坡、風口強陣風與多段攀繩地形，兼具展望與技術體驗。
- **一般路線 vs. 本次分析**：一般山友多由台 20 線臨 105 線 37K 大關山隧道東口（H2722m）起登，採單程 $1.5\text{ km}$ 單日原路往返；而本筆記進一步分析的「[[guanshanling-xitou-mobaolai-xiangyang|關山嶺上溪頭魔保出向陽]]」則是登頂後切入非傳統探勘稜線、串聯巨石瀑、密箭竹海與向陽大崩壁接嘉明湖步道的 D 級 2 日縱走。

---

## 一、路線情境與撤退結構總覽

關山嶺山（H3176m）依行程型態可分為兩種撤退情境：
1. **單攻情境（[[guanshanling|關山嶺山]]傳統步道）**：由台 20 線臨 105 線 37K 大關山隧道東口（H2722m）起登，單程約 $1.5\text{ km}$、爬升約 $431\text{–}454\text{ m}$。因傳統路徑成熟，若遇身體不適、天候惡化或[[ams-protocol|高山反應]]，原則為**原路折返大關山隧道東口**。
2. **縱走情境（[[guanshanling-xitou-mobaolai-xiangyang|關山嶺上溪頭魔保出向陽]]，D 級 2 日）**：過關山嶺山後轉入非傳統探勘稜線，撤退策略並非單純「原路折返」，而是以**[[small-camp-pond|小營地＋池子（`23.27992, 120.96989`）]]**為界，分為「前段原路折返」與「後段單向推進下向陽」兩大階段。

---

## 二、出發前倒隊條件與天候門檻

依據[[2026-11-guanshanling-mobaolai|2026-11 關山嶺上溪頭魔保出向陽]]與[[guanshanling-xitou-mobaolai-xiangyang|路線條目]]，下列狀況應於出發前直接倒隊：
- **寒流條件**：出發前一日發布寒流。
- **降水門檻**：出發前預報過半天數下雪或降雨達 $5\text{ mm/hr}$ 以上。
- **風險主因**：全程含碎石陡坡與[[xitou-mobaolai-bamboo-and-scree|向陽大崩壁邊緣]]，降雨將大幅提高碎石滑動與低溫[[wilderness-medical-protocol|失溫]]風險。

---

## 三、分階段撤退節點與時間停損（Cutoff）

### 1. 日照安全餘裕與瓶頸路段量化
冬季日照短（D1 日落 $T_{\text{sunset}} = 17:12$、D2 日落 $17:11$），為避免摸黑行走非大眾探勘路線，可用日照安全餘裕評估各節點是否準時：

$$T_{\text{margin}} = T_{\text{sunset}} - \left(T_{\text{start}} + \sum_{i} \Delta t_i\right)$$

其中[[xitou-mobaolai-bamboo-and-scree|溪頭山至看天池鞍部密箭竹海]]為全線最大延誤來源，歷史 5 份紀錄實測均值 $\Delta t_{\text{actual}} = 119\text{ min}$，相較企劃預定 $\Delta t_{\text{plan}} = 60\text{ min}$，延誤率達：

$$\delta = \frac{\Delta t_{\text{actual}} - \Delta t_{\text{plan}}}{\Delta t_{\text{plan}}} = \frac{119 - 60}{60} \approx +98.3\%$$

### 2. 四個關鍵撤退與停損節點

| 階段／節點 | 海拔／座標 | 觸發條件（時間／地形／人員） | 撤退或應變方案 | 營地／水源／訊號條件 |
| :--- | :--- | :--- | :--- | :--- |
| **1. 關山嶺山步道段** | H2722m–3176m | 碎石坡體力不濟、天候轉壞或出現[[ams-protocol|AMS]]徵兆 | **原路折返**大關山隧道東口 | 無營地、無水源；稜線展望點 4G／H+ 訊號四格 |
| **2. [[xitou-mountain|溪頭山]]（D1 停損點）** | H3272m | **D1 14:00 前未抵達**，或前段延誤逾 1 小時 | 退回[[xitou-hut-ruins|溪頭山山屋遺址]]（H3150m）紮營迫降，**隔日原路返回**大關山隧道東口（約 2 hr） | 遺址可紮 2–3 頂帳；無活水（僅殘存鐵皮集水不可靠）；溪頭山頂 4G 三格、遺址微弱至無訊號 |
| **3. [[small-camp-pond|小營地＋池子]]（不可逆分界）** | H3180m<br>`23.27992, 120.96989` | 過此點後，因剛下切破碎垂直地形，**逆向重裝爬回溪頭山極度危險** | **單向推進**：除非向陽大崩壁完全無法行走，過此點後皆往前推進由**向陽下山** | 看天池水質呈茶褐色且不穩定，須過濾煮沸 |
| **4. 魔保來叉路口** | H3280m | **D1 16:30 前未抵達** | **不取[[mobaolai|魔保來山]]（H3298m）**，直接前往[[mobaolai-north-camp|北側營地]]紮營避免摸黑 | 營地可搭 3–4 頂四人帳、無活水、無訊號（急用至 `23.28398, 120.973167` 中華有訊號） |

> **大崩壁特殊處置**：若大崩壁路段出現地面持續崩落、碎石滑動或降雨導致路徑破壞無法行走，則撤退原路返回並啟動 D3 預備日下山。

---

## 四、撤退與迫降的資源限制（水、通訊與醫療）

1. **飲水與負重**：[[xiangyang-hut|向陽山屋]]（H2850m）前皆無穩定活水。以 6 人隊伍為例，D1 公水 $6\text{ L}$ 均分加上兩日私水 $3\text{ L}$，個人背負水量為：
   $$W_{\text{water}} = \frac{6\text{ L}}{6} + 3\text{ L} = 4\text{ L}$$
   若啟動預備日原路撤退，須嚴格控管剩餘飲水，必要時過濾煮沸[[mobaolai-north-camp|看天池]]或[[small-camp-pond|小營地池水]]。
2. **通訊與留守**：營地無訊號，急用可移動至 `23.28398, 120.973167`（中華電信）；隊伍建議前、中、壓隊攜帶 3 支無線電（隊內頻道 `145.23 MHz`；救難頻道 `148.74 / 148.77 MHz`；山難救助協會 `145.20 MHz`）。
3. **醫療下撤原則**：若發生 HACE／HAPE 徵兆（參見[[ams-protocol|高山反應處置與預防]]）或中重度[[wilderness-medical-protocol|失溫]]／骨折，**下降高度為最有效處置**；腳踝扭傷依 RICE 原則以八字型包紮固定後評估撤退。

---

## 五、建議參考文獻（待確認後整理進 Wiki）

以下為本次上網搜尋到、**目前尚未整理進 `wiki/`** 的外部參考資料；其中標註「⚠️ 額外新增項目」者，為原 Wiki 未提及之資訊，待你確認後再決定是否納入知識庫：

1. **[玉山國家公園｜南橫三山及關山步道系統—交通方式](https://www.ysnp.gov.tw/Trail/382f4797-1eb1-4746-a122-4e13a9e0c7e4?Tab=4)** & **[公路路況](https://www.ysnp.gov.tw/Highway/C001300)**
   - ⚠️ **額外新增項目（公路管制撤退限制）**：南橫公路「梅山口–向陽」（台 20 臨 105 線 0K–44K）每週**星期二、三、四管制禁止通行**；星期五至星期一僅開放 **07:00–14:00 進入，且 17:00 前必須離開管制路段**（不開放公路健行與腳踏車）。這對「原路撤退至關山嶺山登山口」及「預備日（週一／週二）下山接駁」有決定性影響。
2. **[臺灣登山申請一站式服務網｜南橫三山申辦規定](https://hike.taiwan.gov.tw/news_7_1.aspx?ID=1029)**
   - 說明南橫三山（庫哈諾辛山、塔關山、關山嶺山）皆屬山地管制區與玉山國家公園範圍，關山嶺山僅需入山證、免入園證。
3. **[健行筆記｜南橫埡口段溪頭山縱走關山嶺山](https://hiking.biji.co/index.php?q=review&act=info&review_id=46684)**
   - ⚠️ **額外新增項目（替代路線／O 型接駁）**：記錄由溪頭山登山口（台 20 臨 105 線 38.6K）縱走接關山嶺山出大關山隧道埡口之走法，可作為只走前段時不用走回頭路的參考方向。
4. **[Hikingbook｜關山嶺山-溪頭山-魔保來山-向陽縱走](https://zh-tw.hikingbook.net/hikes/%E9%97%9C%E5%B1%B1%E5%B6%BA%E5%B1%B1-%E6%BA%AA%E9%A0%AD%E5%B1%B1-%E9%AD%94%E4%BF%9D%E4%BE%86%E5%B1%B1-%E5%90%91%E9%99%BD%E7%B8%B1%E8%B5%B0-b6dd18da)**
   - 記錄初中階探勘路段實際路況：箭竹坡陡上、碎石坡橫渡與大落差上攀，第二天魔保來至向陽亦較一般百岳路線難走。
5. **[關山嶺山 — 維基百科](https://zh.wikipedia.org/zh-tw/%E9%97%9C%E5%B1%B1%E5%B6%BA%E5%B1%B1)**
   - ⚠️ **額外數據差異**：維基百科標註關山嶺山最高點海拔為 `3,173.7 m`，與企劃書常用之 `3,176 m` 略有差異，待確認是否於 `guanshanling.md` 併記。
