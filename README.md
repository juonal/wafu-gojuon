# 和風五十音

日文平假名・片假名互動自學工具，針對平板觸控與觸控筆設計（以小米 Pad 8 Pro 為主要測試尺寸）。可加到主畫面，離線也能使用。

線上版：https://juonal.github.io/wafu-gojuon/

## 功能

- **五十音圖表**：清音、濁音・半濁音、拗音三張表。點「行」或「段」標題可連續朗讀；點清音可看漢字字源（女手／男手）、記憶口訣與代表單字。
- **手寫描字**
  - 筆順描紅與每筆起點編號，可播放筆順動畫
  - 兩個步驟：先照描紅寫，再不看描紅默寫，筆畫數正確才蓋「花丸」
  - 偵測到觸控筆後自動忽略手指與手掌誤觸；支援筆壓粗細
  - 「四個房間」、米字格、無格線三種格線
- **測驗與歌牌**
  - 日式歌牌（かるた）聽音搶答，干擾牌會放入形近字
  - 分組測驗：清音、濁音、拗音都可選；含易混淆特訓與錯題複習
  - 4×4 翻牌配對
- **短句跟讀**：打招呼、旅遊會話、歌詞短句；助詞「は／へ／を」正確標成 wa／e／o。可貼上自訂日文。
- **旅遊單字**：基本用語、交通、餐廳、購物、住宿、觀光、緊急狀況、數字・時間，共 98 個初學者單字。可瀏覽、朗讀、標記「已記住」，也有字卡練習（日→中、中→日）。
- **進度與攻略**：花丸統計、測驗正確率、歌牌紀錄；錯題依 1、3、7、14 天間隔安排複習。

## 使用說明

- 在平板的 Chrome 開啟網址，選單中選「加到主畫面」或「安裝應用程式」，之後就能像 App 一樣全螢幕使用，離線也能開。
- 日語朗讀使用瀏覽器內建語音。若沒有聲音，請到 Android「設定 → 文字轉語音輸出」確認已安裝 Google 語音服務的日文語音。
- 學習進度只存在本機瀏覽器（localStorage），不會上傳或跨裝置同步。清除瀏覽器資料會一併清除進度。

## 修改與部署

網站本身是靜態檔案，直接放在 GitHub Pages 即可：

| 檔案 | 用途 |
| --- | --- |
| `index.html` | 主程式（HTML、CSS、JavaScript、假名與單字資料） |
| `tailwind.css` | 預先編譯好的 Tailwind CSS |
| `src/input.css` | Tailwind 設定（顏色、字型） |
| `sw.js`、`manifest.webmanifest`、`icons/` | 離線使用與加到主畫面 |

如果修改了 `index.html` 裡的 Tailwind class，需要重新產生 `tailwind.css`：

```bash
npm install --no-save @tailwindcss/cli@4 tailwindcss@4
npx @tailwindcss/cli -i src/input.css -o tailwind.css --minify
```

更新網站內容後，請把 `sw.js` 裡的 `CACHE_VERSION` 改成新值（例如 `v2`），已安裝的使用者下次開啟時才會拿到新版。

## 使用的資源與授權

- 筆順資料：[KanjiVG](https://kanjivg.tagaini.net/) © Ulrich Apel，採 [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/) 授權。內嵌於 `index.html` 的 `KANA_STROKES`，該部分資料沿用相同授權。
- 字型：[Klee One](https://fonts.google.com/specimen/Klee+One)（教科書體風格）、Noto Sans JP／TC、Noto Serif JP，皆為 SIL Open Font License。
- [Tailwind CSS](https://tailwindcss.com/)（MIT）

本專案其餘程式碼尚未指定授權條款。
