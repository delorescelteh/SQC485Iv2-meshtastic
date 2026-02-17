# 快速開始

## 你需要的東西

- macOS + PlatformIO (`pio`)
- 兩台 Heltec HT62（ESP32‑C3 + SX1262）
- 兩個 CH340 USB-Serial（或板子自帶 CH340），在 macOS 會出現類似：
  - `/dev/cu.usbserial-21220`
  - `/dev/cu.usbserial-21230`
- SX1262 天線 *務必接上*

## 一次跑通（建議流程）

1. Clone Meshtastic-device（或使用既有 repo）
2. 用正確 env 編譯：`heltec-ht62-esp32c3-sx1262`
3. 如果刷機不穩（常見），把 `upload_speed` 降到 **115200**
4. 逐台刷入（一次只刷一台，避免混亂）
5. 設定 LoRa Region（以 Taiwan/TW 為例）
6. 用 CLI 驗證兩台 **LoRa 廣播訊息**可雙向互通

各步驟詳見後續章節。
