---
name: yamaha-network-docs
description: >-
  ヤマハネットワーク機器（RTX/NVR/vRX ルーター、SWX スイッチ、WLX 無線AP）の YAMAHA コマンド
  リファレンスと設定例集を、出典URL付きで参照・引用する。コマンドの書式・初期値・適用モデルを
  調べるとき、設定例を探すとき、config を読む・書く・レビューするときに使う。「ヤマハ」「RTX」
  「SWX」「WLX」「RTpro」「コマンドリファレンス」「設定例」が出てきたら参照する。
---

# ヤマハネットワーク機器ドキュメント参照

ヤマハの CLI は独自構文で、書式・初期値・対応機種はファームのリビジョンで変わる。
記憶や他社 CLI からの類推で答えず、YAMAHA のページを取得して裏取りし、本文を取得したページの URL を出典として示す。

## コマンドリファレンス（`https://www.rtpro.yamaha.co.jp/RT/manual/<base>/`）

`<base>` は機種で決まる。主な対応は次のとおりで、旧機種や全機種の対応表は `references/url-map.md` にある。

- `rt-common`: vRX、RTX840/3510/1300/1220/830/1210/5000/3500
- `nvr700w_nvr510`: NVR700W/NVR510（rt-common とは別）
- `swx<型番>/cmdref`: スイッチは機種別（例 `swx2320/cmdref` は SWX2320 と SWX2322P）
- `wlx-common`: WLX413/333/232/323/322/222/212。WLX402/313/302 は機種別の `wlx402` などを使う

`index.html` は frameset なので、取得しても本文は空になる。代わりに次を使う。

1. `<base>/cmdref_index.html`: コマンド名の索引。各コマンドのページへの相対リンクがある。最初にこれを取得する。
2. `<base>/toc.html`: 章立ての目次。カテゴリ単位で見渡すときに使う。
3. `<base>/Cmdref.pdf`: 全文 PDF。数百ページあるので、必要な章だけを読む。

コマンドのページには [書式] [設定値及び初期値] [説明] [ノート] [設定例] [適用モデル] がある。
rt-common は複数機種の共通版なので、[適用モデル] と [ノート] にある機種・リビジョンごとの制約を対象機種と照合する。

## 設定例集（`https://network.yamaha.com/setting`）

通常の HTML ページ。カテゴリ一覧（`/setting/<category>/<topic>`）から、使用機種が合う例を選んで個別ページを開く。
個別ページの URL は一覧のリンクから取り、推測で組み立てない。

## ページが見つからないとき

`site:rtpro.yamaha.co.jp/RT/manual/<base> <キーワード>` や `site:network.yamaha.com/setting <キーワード>` で検索する。
リリースノートや技術資料などの入口は `references/url-map.md` にある。
