# Source / provenance

このリポジトリは、SourceForgeから取得した **Apple WLOC v1.1.0 source code.zip** を基準に復元しています。

## 元ソース

- SourceForge mirror: https://sourceforge.net/projects/apple-wloc.mirror/
- 元GitHub: `Yu9191/wloc`
- 対象コミット: `ecd4992a7c92b7d6e92eb80b948eba54202ab85a`
- コミット日時: 2026-08-08

## SourceForge v1.1.0で確認したSHA-256

```text
wloc.js
a1b361e60f0b434585260fb59c65d1ddbe3bff89ace3639f592e7d8af432b3c1

wloc-settings.js
433073eed20064ee59cafc857eb444e0bcc958290323ac7586a77093776d8f42

wloc.module（元ファイル）
06acd0530cef9bf0e5bd460ac3f7b95179e09edb29406d43cf2f66ccaebc4071
```

## 取り込み方法

`.github/workflows/vendor-wloc.yml` が元コミットから以下を取得します。

- `dist/wloc.js`
- `dist/wloc-settings.js`
- `source/wloc.module.original`

取得後に上記SHA-256を検証し、一致したファイルだけをこのリポジトリへコミットします。

Shadowrocket用の `modules/wloc.module` は、実行スクリプトとしてこのリポジトリ自身の `dist/` を参照します。
