# 疑難排解

## 刷機：No serial data received / Unable to verify flash chip connection

常見原因：
- 板子沒進 bootloader/下載模式
- 921600 upload_speed 不穩
- USB 線/Hub 不穩、供電不足

處理：
- 一次只插一台板子
- 依板子操作進 bootloader
- 把 `upload_speed` 降到 **115200** 再刷

## Port busy / Resource busy

表示該序列埠被其他程式佔用：
- PlatformIO monitor
- Arduino Serial Monitor / CoolTerm
- `screen` / 其他工具

把佔用程式關掉再重試。

## 兩台都正常開機但互收不到

優先檢查：
- SX1262 天線是否確實接上
- 兩台是否設定相同 Region、相同 channel/PSK
- 擺位/距離（先近距離、避開金屬遮蔽）

## 直傳遇到 PKI_SEND_FAIL_PUBLIC_KEY

直傳/ACK 可能需要公鑰交換或安全設定。
建議先用廣播雙向驗證 LoRa link，再處理 PKI。
