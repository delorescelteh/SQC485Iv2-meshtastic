# Pinout 抽取工作流程（POW_IN / CONN2）

目的：提供**可重複**的抽取步驟與輸出格式，降低原理圖閱讀誤差，方便後續回寫 `docs/hardware_pinout.md` 與 `docs-meshtastic/docs/hardware.md`。

## 建議工具（不需額外安裝）
- **macOS Preview**（內建）：可放大、標註、截圖
- **Windows**：Edge / Acrobat Reader

## 輸出檔案與命名
- 原理圖截圖：`assets/schematics/YYYYMMDD_pow_in_page.png`
- 抽取表：`docs-meshtastic/docs/pinout_extraction_notes.md`
- 最終回寫：`docs/hardware_pinout.md` + `docs-meshtastic/docs/hardware.md`

## Step-by-step
1. **定位原理圖頁**
   - 開啟 `docs-meshtastic/assets/SCH_SQC485ISv200_2026-02-05.pdf`
   - 搜尋或翻到含 **POW_IN / CONN2** 的頁面
2. **放大與截圖**
   - 針對每個連接器區塊放大至腳位標示清晰可讀
   - 以系統截圖存成 `assets/schematics/YYYYMMDD_pow_in_page.png`
3. **逐 pin 抄錄**
   - 依 `docs-meshtastic/docs/pinout_extraction_notes.md` 表格格式填入：
     - Pin 編號
     - Signal 名稱
     - Net / MCU 對應
     - 備註（例如：方向、GND/VIN、疑似對接）
4. **交叉比對**
   - 若 net 名稱對應到 MCU GPIO，補上 GPIO 編號
   - 遇到不確定之處，保留 `?` 並在備註註明疑點
5. **回寫文件**
   - 將確認後的 POW_IN / CONN2 pin 表填入：
     - `docs/hardware_pinout.md`
     - `docs-meshtastic/docs/hardware.md`

## 品質檢查（最小驗收）
- 每個 pin 都有 **來源截圖檔名** 或頁碼
- POW_IN / CONN2 至少各完成一列完整記錄
- `docs/hardware_pinout.md` 的對應表不再出現 `TBD`

## 常見錯誤避免
- **腳位方向誤判**：若有絲印或箭頭，請在備註標示方向
- **相似網名混淆**：例如 `GND` vs `GNDA`，需保留原始標示
- **多人同時編輯**：先在 `pinout_extraction_notes.md` 彙整，再統一回寫
