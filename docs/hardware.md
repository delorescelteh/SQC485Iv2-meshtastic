# SQC485Iv2 硬體/Pinout（待補齊）

> 目前我已從 workspace 的原理圖 PDF 抓到「主要零件/網名/模組腳位清單」；
> 但要做到完整 pinout（對應到 Meshtastic variant / board env）還需要把每條 net 再整理成表格。
>
> 原理圖（公開）放在本 repo：`assets/SCH_SQC485ISv200_2026-02-05.pdf`

## 供電架構（從原理圖文字可確認）

- **USB Type‑C** 供電輸入（VUSB/USB_5V）
- 外部電源端子 `POW_IN`（原理圖註記："POWER input (30 ~ 8 V) buck to 3V3"）
- 降壓：`U2 BL9342` + `L1 4.7uH`（buck 轉 3V3）
- 充電：`U4 TP4054`（18650 單節鋰電充電 IC）
- 電池座：`BT1/BT2 MY-ZJ-110`（18650）
- 3V3 LDO：`U3 XC6206P332MR`

## 主要模組

- `U1 HT-CT62`（ESP32‑C3 + SX1262 模組/板）
  - 腳位文字（原理圖上可讀到）：
    - GPIO0..GPIO10（含 EN）
    - GPIO18, GPIO19
    - RXD, TXD
    - LoRa.ANT
    - 另有 `2.4G_ANT`、`LoRa.ANT` 標示

## Meshtastic（SX1262）腳位對應（已落地到韌體 variant）

此對應目前採用 **HT-CT62 參考設計相容**的定義（已放進韌體 fork 的 `variants/esp32c3/sqc485iv2/variant.h`）：

- `BUTTON_PIN` = **GPIO9**（原理圖 net：`GPIO9_USER_KEY`）
- LED
  - `LED_POWER` = **GPIO2**（原理圖註記：GPIO2 = LOW 時 LED 亮）

SX1262：
- `LORA_SCK`  = **GPIO10**
- `LORA_MISO` = **GPIO6**
- `LORA_MOSI` = **GPIO7**
- `LORA_CS`   = **GPIO8**
- `LORA_DIO1` = **GPIO3**
- `LORA_RESET`= **GPIO5**
- `LORA_BUSY` = **GPIO4**
- `SX126X_DIO3_TCXO_VOLTAGE` = **1.8V**

> 以上這組腳位也與我們先前從開機 log 看到的 `SPI.begin(SCK=10, MISO=6, MOSI=7, NSS=8)` 一致。

## 電池量測（Battery measurement）

- 依你目前的描述：**此板沒有 ADC 做電池電壓量測**。
- 因此文件與韌體目前都不假設有電池電壓讀值（不做電量百分比顯示/校正）。
- 如果未來硬體版本要加電量量測，建議走：
  - 簡單：分壓到 ESP32-C3 ADC pin
  - 更準：加 fuel gauge（例如 MAX17048/MAX17049）走 I2C

## 介面

- RS485：`U5 SN65HVD1780DR`
  - 看到 `A/B` 差分線與 `DE/#RE` 控制線標示

- I2C/UART 擴展端子：`CONN2 1.25-4PWB`
  - 原理圖上可見 net：`GND`, `3V3`, `LORA_RXD_SDA`, `LORA_TXD_SCL`
  - 命名暗示可作 UART（RXD/TXD）或 I2C（SDA/SCL）用途（待你確認最終定義）

## 使用者按鍵 / 指示

- 看到 `GPIO9_USER_KEY`、`GPIO2`（並註記："LED W on when GPIO2 = LOW"）

## TODO（我下一步要補）

- 把 **HT-CT62 的 GPIO 與 SX1262 的 SPI/IRQ/RESET/BUSY** 對應整理成表格
- 把 `POW_IN` 端子各 pin 定義（GND/VIN/RS485?）整理成表格
- 用整理後的 pinout 在韌體 repo 裡新增真正的 `SQC485Iv2` variant（而不是暫時的 HT62-compatible env）
