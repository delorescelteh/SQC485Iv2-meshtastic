# 釋出預編譯韌體（GitHub Releases）

目標：讓 DIY 使用者不用裝 PlatformIO，就能直接下載 `.bin` / `.factory.bin` 來刷機。

## 建議做法

- 建一個 **fork repo**（例如：`delorescelteh/SQC485Iv2-Meshtastic-device`）
- 用 GitHub Actions 在 **tag** 時自動編譯，並把產物上傳到 Release

## 已建立的 Workflow

在韌體 repo 內：

- `.github/workflows/release-sqc485iv2.yml`

目前設定：
- push tag `sqc485iv2-v*` 觸發
- 先以 PlatformIO env `heltec-ht62-esp32c3-sx1262` 編譯（待 SQC485Iv2 pinout 確認後再換成專屬 env）
- 打包 `.pio/build/<env>/` 下的 `.bin` 與 `.factory.bin`
- 產生 `SHA256SUMS.txt`

## 如何發一個 Release（範例）

在韌體 repo：

```bash
git tag sqc485iv2-v0.1.0
git push origin sqc485iv2-v0.1.0
```

Actions 跑完後會自動建立 GitHub Release，並附上可下載檔案。
