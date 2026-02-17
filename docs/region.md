# 設定 LoRa Region（Taiwan/TW）

> 重要：請依所在地法規設定正確 Region。

如果兩台都維持 `UNSET`，實測可能導致互通測試不穩定或不易診斷。

## 用 Meshtastic CLI（走 USB 序列埠）設定

建議用 `pipx` 或 venv 安裝 `meshtastic` CLI。

設定 Taiwan：

```bash
meshtastic --port /dev/cu.usbserial-21220 --set lora.region TW
meshtastic --port /dev/cu.usbserial-21230 --set lora.region TW
```

重開機（建議）：

```bash
meshtastic --port /dev/cu.usbserial-21220 --reboot
meshtastic --port /dev/cu.usbserial-21230 --reboot
```

確認：

```bash
meshtastic --port /dev/cu.usbserial-21220 --get lora.region
meshtastic --port /dev/cu.usbserial-21230 --get lora.region
```
