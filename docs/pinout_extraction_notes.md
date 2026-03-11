# SQC485I Sv2.0 腳位抽取筆記

目的：從原理圖 PDF 中抽出 **POW_IN / CONN2** 的腳位表，建立單一可信的 pinout 對照。

## 來源文件
- `docs-meshtastic/assets/SCH_SQC485ISv200_2026-02-05.pdf`

## 抽取清單（待填）
> 建議以「連接器標號 → 信號名稱 → MCU 腳位/網名」三欄整理，避免多版本混淆。

### POW_IN
| Pin | Signal | Net / MCU | 備註 |
| --- | --- | --- | --- |
|  |  |  |  |

### CONN2
| Pin | Signal | Net / MCU | 備註 |
| --- | --- | --- | --- |
|  |  |  |  |

## 抽取步驟建議
1. 先定位 PDF 中的 **連接器頁**（POW_IN、CONN2）
2. 逐 pin 抽出 **信號名稱** 與 **連接網名**
3. 若網名對應 MCU 腳位，補上對應（例如：`GPIOxx`）
4. 完成後回寫 `docs/hardware.md` 的 pin tables

## 後續更新點
- `docs/hardware.md`：更新 POW_IN / CONN2 pin tables
- `variants/esp32c3/sqc485iv2/variant.h`：依確認後 pinout 修正
