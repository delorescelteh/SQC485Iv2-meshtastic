# 燒錄（含降速到 115200）

## 1) 先一次只插一台

避免兩台同時連線造成混亂（尤其是你要手動進 bootloader 時）。

## 2) 進入 ESP32-C3 bootloader（下載模式）

常見方式：

- 按住 **BOOT**
- 點一下 **RST**（或重新插 USB）
- 再放開 BOOT

> 具體按鍵名稱依板子絲印可能不同。

## 3) 用 PlatformIO 上傳

```bash
pio run -e heltec-ht62-esp32c3-sx1262 -t upload --upload-port /dev/cu.usbserial-21230
```

## 4) 若遇到 No serial data received / 921600 不穩：把 upload_speed 降到 115200

在 Meshtastic-device repo 裡找到該板子的 env 定義檔（本次實測位置）：

- `variants/esp32c3/heltec_esp32c3/platformio.ini`

把：

```ini
upload_speed = 921600
```

改成：

```ini
upload_speed = 115200
```

再重刷一次通常就會穩。

## 5) 兩台都刷完

第一台成功後，換第二台重複上述步驟。
