# Meshtastic Heltec-C3 (ESP32-C3 + SX1262) 編譯/燒錄/互通測試（macOS）

這份指南記錄如何在 macOS 上：

- 用 PlatformIO 編譯 Meshtastic-device
- 透過 CH340 USB 串口燒錄到兩台 Heltec HT62 (ESP32‑C3 + SX1262)
- 設定 LoRa Region（以 Taiwan / TW 為例）
- 驗證兩台節點可互相收發訊息

> 適用情境：你在一台 Mac（例如 Mac mini）上同時插著兩個 CH340 串口裝置。

## 目錄

請看 `docs/SUMMARY.md`
