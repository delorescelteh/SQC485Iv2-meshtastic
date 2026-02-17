# 環境準備

## 安裝 PlatformIO

確認 `pio` 可用：

```bash
pio --version
```

## 取得 Meshtastic-device

```bash
git clone https://github.com/meshtastic/Meshtastic-device.git
cd Meshtastic-device
# 建議用 develop（依你的需求）
```

## 找到正確的 PlatformIO environment

Heltec HT62 (ESP32-C3 + SX1262) 對應 env：

- `heltec-ht62-esp32c3-sx1262`

你也可以用：

```bash
pio project config --json-output | jq '.envs'
```

## 找到序列埠

在 macOS 上通常用 `ls /dev/cu.usbserial-*`：

```bash
ls -1 /dev/cu.usbserial-*
```

會看到類似：

- `/dev/cu.usbserial-21220`
- `/dev/cu.usbserial-21230`
