# Apple WLOC – Shadowrocket用ミラー

これは SourceForge の **Apple WLOC v1.1.0 mirror** から復元した、iPhone / Shadowrocket 用の個人ミラーです。

- 元プロジェクト: `Yu9191/wloc`
- 元コミット: `ecd4992a7c92b7d6e92eb80b948eba54202ab85a`
- 保存元: https://sourceforge.net/projects/apple-wloc.mirror/
- 用途: Apple のネットワーク測位（Wi‑Fi / 基地局）の返却座標を Shadowrocket で書き換える

## Shadowrocketへの追加URL

以下を Shadowrocket の **配置 → モジュール → ＋ → URLから追加** に貼り付けます。

```text
https://raw.githubusercontent.com/atsu6/wloc/main/modules/wloc.module
```

追加後、`Apple WLOC 定位修改` を有効にしてください。

## HTTPS復号の設定

Shadowrocketで HTTPS Decryption / HTTPS 解密を有効にし、CA証明書を生成・インストールします。

iPhone側で:

1. 設定 → 一般 → VPNとデバイス管理 → Shadowrocket証明書をインストール
2. 設定 → 一般 → 情報 → 証明書信頼設定
3. ShadowrocketのCAを「完全に信頼」にする

WLOCモジュールがMITMする対象は次の2ホストです。

```text
gs-loc.apple.com
gs-loc-cn.apple.com
```

## 位置を変更する

ショートカット:

- 設定: https://www.icloud.com/shortcuts/a82717d8fdad4e6280866fcf911173f7
- 復元: https://www.icloud.com/shortcuts/f42632d406504f24a2cd163af4fe012f

Appleマップで場所を長押し → 共有 → `wloc 设置地理位置` を実行します。

反映されない場合は位置情報サービスをOFF/ONし、それでも変わらなければiPhoneを再起動してください。

## 注意

これはGPSチップそのものを書き換えるものではなく、Appleのネットワーク測位レスポンスを書き換える方式です。アプリによってはGPS等の別情報を使うため、位置が変わらない場合があります。

またHTTPS復号用CAを信頼するため、使わないときはWLOCモジュールまたはHTTPS復号をOFFにする運用を推奨します。

## ファイル

- `modules/wloc.module` – Shadowrocket用モジュール
- `dist/wloc.js` – WLOCレスポンス書換えスクリプト
- `dist/wloc-settings.js` – 座標保存スクリプト
- `SOURCE.md` – 元ソースの来歴・照合情報
