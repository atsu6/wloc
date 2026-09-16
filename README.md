# Apple WLOC – Shadowrocket用ミラー

SourceForge の **Apple WLOC v1.1.0 mirror** を基準にした、iPhone / Shadowrocket 用の個人ミラーです。

- 元プロジェクト: `Yu9191/wloc`
- 元コミット: `ecd4992a7c92b7d6e92eb80b948eba54202ab85a`
- 保存元: https://sourceforge.net/projects/apple-wloc.mirror/
- 用途: Apple のネットワーク測位（Wi‑Fi / 基地局）の返却座標を Shadowrocket で書き換える

## 1. Shadowrocketへ追加

Shadowrocket の **配置 → モジュール → ＋ → URLから追加** に、これを貼り付けます。

```text
https://raw.githubusercontent.com/atsu6/wloc/main/modules/wloc.module
```

追加された **Apple WLOC 定位修改** をONにします。

## 2. HTTPS復号を有効化

Shadowrocketで **HTTPS Decryption / HTTPS 解密** をONにし、CA証明書を生成・インストールします。

iPhone側で:

1. 設定 → 一般 → VPNとデバイス管理 → Shadowrocket証明書をインストール
2. 設定 → 一般 → 情報 → 証明書信頼設定
3. ShadowrocketのCAを「完全に信頼」ON

対象ホスト:

```text
gs-loc.apple.com
gs-loc-cn.apple.com
```

## 3. 位置変更用ショートカット

- **位置を設定**: https://www.icloud.com/shortcuts/a82717d8fdad4e6280866fcf911173f7
- **元に戻す**: https://www.icloud.com/shortcuts/f42632d406504f24a2cd163af4fe012f

Appleマップで目的地を長押し → **共有** → `wloc 设置地理位置` を実行します。

反映されない場合は、位置情報サービスをOFF/ON。それでも変わらなければiPhoneを再起動します。

## このリポジトリだけで動作します

`modules/wloc.module` は次の2ファイルを **この `atsu6/wloc` リポジトリから直接読み込みます**。

```text
https://raw.githubusercontent.com/atsu6/wloc/main/dist/wloc.js
https://raw.githubusercontent.com/atsu6/wloc/main/dist/wloc-settings.js
```

`dist/` の2ファイルは、元コミット `ecd4992...` から取得した後、SourceForge v1.1.0で確認したSHA-256と一致した場合だけGitHub Actionsが保存する構成です。

元の `wloc.module` も `source/wloc.module.original` として保存しています。照合情報は [`SOURCE.md`](SOURCE.md) を参照してください。

## 注意

これはGPSチップそのものを書き換えるものではなく、Appleのネットワーク測位レスポンスを書き換える方式です。アプリによってGPS等の別情報が優先される場合があります。

またHTTPS復号用CAを信頼するため、使わないときはWLOCモジュールまたはHTTPS復号をOFFにする運用を推奨します。
