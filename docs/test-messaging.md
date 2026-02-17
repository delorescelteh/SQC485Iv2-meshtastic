# 兩台節點互通測試（廣播/直傳/ACK）

## 先做「廣播訊息」驗證（最可靠）

1) 讓 B（接收端）listen：

```bash
meshtastic --port /dev/cu.usbserial-21230 --listen
```

2) 從 A（發送端）送廣播：

```bash
meshtastic --port /dev/cu.usbserial-21220 --dest '^all' --sendtext "hello-A-to-all"
```

若 B 端看到收到 `TEXT_MESSAGE_APP`，且 transport 為 `TRANSPORT_LORA`，代表 A→B LoRa 正常。

反向再做一次（B→A）：

```bash
# A listen
meshtastic --port /dev/cu.usbserial-21220 --listen

# B broadcast
meshtastic --port /dev/cu.usbserial-21230 --dest '^all' --sendtext "hello-B-to-all"
```

## 直傳（指定 dest）與 ACK

取得對方節點 ID（例如 `!7d51bb04`）後：

```bash
meshtastic --port /dev/cu.usbserial-21220 --dest '!7d51bb04' --sendtext "direct" --ack --timeout 30
```

### 若遇到 `PKI_SEND_FAIL_PUBLIC_KEY`

代表直傳/ACK 可能受到 PKI/公鑰交換機制影響。

建議：
- 先確認「廣播」雙向通，再處理 PKI/安全設定
- 用手機 App / Meshtastic Web 介面檢查安全/加密相關選項
- 或先走同頻道廣播聊天，等節點互相學到對方資訊後再試直傳
