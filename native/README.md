# 早口言葉チャレンジ iOS版（Capacitorラッパー）

本体は リポ直下のPWA（index.html ほか）。このフォルダはそれをiOSアプリに包むための器。

## 仕組み
- `copy-www.sh` … リポ直下のPWAファイルを `www/` にコピーする（www/ はgit管理外・生成物）
- Capacitor 8（SPM方式・CocoaPods不要）＋ @capacitor/local-notifications
- ネイティブ価値: 毎朝8時「今日の早口言葉」ローカル通知（index.html内・ネイティブ実行時のみ発動）
- Bundle ID: `com.experisent.hayakuchi`

## 本体を更新したらiOSに反映する手順
```sh
cd native
./copy-www.sh
npx cap sync ios
npx cap open ios   # Xcodeが開く → 実行 or Archive
```

## 初回セットアップ（Xcode側）
1. Xcode → Settings → Accounts → 組織用Apple IDでサインイン
2. App target → Signing & Capabilities → Team = EXPERISENT / Automatically manage signing ON
3. 実機 or シミュレータで Run → TestFlightは Product > Archive → Distribute

## 審査提出時の必須設定（忘れ厳禁）
- App Store Connect で **EU配信オフ＋非trader申告**（住所・電話の公開回避。詳細: Vault `06_Projects/20260628_AppleDeveloper組織登録/経緯と設計.md`）
- 審査メモ: 「録音・採点・連続記録・オフライン動作は端末内で完結」
