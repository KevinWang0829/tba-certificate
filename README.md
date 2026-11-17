# TBA · TWB 完騎證書

2026 年 TBA 與 TWB 兩個場次的四極、雙塔、北高**非官方**完騎紀念證書產生器。純靜態網頁，不需要後端。

- 輸入號碼或姓名頭尾字查成績，或自己填各點時間、丟 GPX 推算
- 名次依公開成績的晶片時間即時計算
- 輸出 A4、300 dpi 的 PNG

## 設計

整張證書由上到下就是那趟路：位置對應緯度，底色是騎到那個緯度時的天色，所以每個人的證書都不一樣。燈塔只有在夜裡經過時才亮；北高沒有燈塔，起終點畫成兩座城的燈火。

## 資料

- `results-620.json`、`results-520.json`、`results-360.json`：擷取自 [iRunner 公開成績](https://irunner.biji.co/track/1581/real-time-ranking)（2026-11-17），姓名遮住中間字。每列為 `[號碼, 姓名, 組別, 出發時刻, 各感應點累計秒數…]`。
- TWB 場次只開放用晶片號碼逐筆查詢，本專案不存 TWB 的成績：使用者按查詢時，網頁才向 TWB 自己的查詢服務問那一筆。
- 正式成績以主辦單位公告為準。本專案與中華民國自行車協會、台灣自行車協會、iRunner 無關。
- 大字的逐筆明體字形來自 [GlyphWiki](https://glyphwiki.org/)，以 [KAGE engine](https://github.com/kurgm/kage-engine) 展開後內嵌。

## 本機預覽

```
python3 -m http.server 8000
```

然後開 <http://localhost:8000>。直接用 `file://` 開會讀不到成績檔。
