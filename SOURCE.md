# Source / provenance

このリポジトリのShadowrocket用設定は、SourceForgeから取得した **Apple WLOC v1.1.0 source code.zip** を基準に確認しています。

## 元ソース

- SourceForge mirror: https://sourceforge.net/projects/apple-wloc.mirror/
- 元GitHub: `Yu9191/wloc`
- 対象コミット: `ecd4992a7c92b7d6e92eb80b948eba54202ab85a`
- コミット日時: 2026-08-08

## ZIP内ファイルのSHA-256

```text
wloc.js
A1B361E60F0B434585260FB59C65D1DDBE3BFF89ACE3639F592E7D8AF432B3C1

wloc-settings.js
433073EED20064EE59CAFC857EB444E0BCC958290323AC7586A77093776D8F42

wloc.module（元ファイル）
06ACD0530CEF9BF0E5BD460AC3F7B95179E09EDB29406D43CF2F66CCA EBC4071
```

`wloc.module` の正規SHA-256は次です。

```text
06acd0530cef9bf0e5bd460ac3f7b95179e09edb29406d43cf2f66ccaebc4071
```

元 `modules/wloc.module` は消滅した `Yu9191/wloc` の `main` を参照していたため、このリポジトリの `modules/wloc.module` では、同内容が確認できるミラーの **不変コミット `ecd4992...`** をscript-pathに固定しています。

これにより、Shadowrocketへ追加する入口URLは `atsu6/wloc` 固定になります。
