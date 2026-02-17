# SQC485Iv2 板子簡介

SQC485Iv2 是一塊適合做 **Meshtastic 太陽能固定節點** 的 DIY 板，硬體重點：

- MCU/LoRa：**ESP32‑C3 + SX1262**
- 供電：
  - USB 5V 供電
  - **8V–24V** 外部輸入（適合太陽能板/充電系統）
  - **18650 電池槽**（行動/備援）

> 這份文件專注在「韌體編譯/燒錄/測試/釋出」。
> 硬體原理圖/Pinout 會在硬體資料確認後補上。

## 相關 Repo

- 韌體（fork）：`delorescelteh/SQC485Iv2-Meshtastic-device`
- 文件（GitBook 用）：`delorescelteh/SQC485Iv2-meshtastic`

