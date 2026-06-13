---
name: yamaha-network-docs
description: >-
  ヤマハネットワーク機器（RTX/NVR/vRX ルーター、SWX スイッチ、WLX 無線AP）の YAMAHA コマンド
  リファレンスと設定例集を、出典URL付きで参照・引用する。コマンドの書式・初期値・適用モデルを
  調べるとき、設定例を探すとき、config を読む・書く・レビューするときに使う。「ヤマハ」「RTX」
  「SWX」「WLX」「RTpro」「コマンドリファレンス」「設定例」が出てきたら参照する。
---

# ヤマハネットワーク機器 ドキュメント参照

RTX/NVR/vRX ルーター、SWX スイッチ、WLX 無線AP の YAMAHA コマンドリファレンスと設定例集から、
正確な情報を出典URL付きで取得する。記憶や他社機器（Cisco/Juniper 等）の知識でコマンドを
推測しない。ヤマハのコマンド体系は独自で、書式・初期値・適用モデルは一次情報でしか確定できない。
必ず YAMAHA のページを fetch して裏取りする。

## iframe(frameset) の罠

YAMAHA のコマンドリファレンスは `www.rtpro.yamaha.co.jp` 上の frameset ページで構成される。
`.../index.html` を fetch しても本文は空（タイトルのみ）で、内容は得られない。
ここでつまずきやすい。次を守る。

- `.../index.html`（frameset）は本文取得に使わない。
- 個別コマンドの「リーフページ」を直接 fetch する。リーフは通常HTMLとして正しく取得でき、
  書式・初期値・適用モデルまで構造化されている。URL は下記の3経路で得る。
- もしくは全文PDF（`Cmdref.pdf`）を fetch する。frameset を経由しないので確実。

リーフページの URL さえ得られれば本文は取れる。課題は「リーフURLをどう知るか」だけで、
それを解決するのが下記の3経路。

## 2つのサイトの役割

| サイト | 役割 | ページ形式 | fetch |
|---|---|---|---|
| `www.rtpro.yamaha.co.jp` | コマンドリファレンス、ファーム、リリースノート | frameset（index は空） | リーフ/PDF は可、index は不可 |
| `network.yamaha.com` | 設定例集、製品情報、知識&技術 | 通常HTML | 可 |

rtpro は `http://` で案内されることが多いが `https://` でも到達できる。fetch は `https://` を優先する。

## デバイスとリファレンスの対応

3系統で参照先が異なる。取り違えると見つからない。

| 機器系統 | 例 | リファレンス基点 |
|---|---|---|
| ルーター RTX/NVR/vRX | RTX1300, RTX830, RTX1220, NVR700W, NVR510, vRX | `rt-common`（全機種共通。リーフも配下） |
| スイッチ SWX | SWX2310P, SWX2310, SWX3220, SWX2322P | 機種別 `<model>/cmdref`（例 `swx2310p`） |
| 無線AP WLX | WLX323, WLX322, WLX222, WLX212, WLX402, WLX313 | 機種別 `<model>/<category>` ＋共通 `wlx-common`（frameset/PDF） |

- ルーターは `rt-common` に全機種分が載り、各コマンドの「適用モデル」欄で機種ごとの可否を区別する。
  リーフHTMLも `rt-common/...` 配下にある。
- スイッチは機種ごとに別リファレンス。型番を小文字にしてディレクトリ名にする（`swx2310p/cmdref/...`）。
- 無線APは注意が必要。共通の `wlx-common`（frameset と全文PDF）がある一方、個別コマンドの
  リーフHTMLは機種別ディレクトリ（例 `wlx302/airlink/airlink_ssid.html`）に置かれる。
  機種プレフィックスが変わるため、URLを手で組み立てず経路A（検索）で実URLを特定する。

詳細なURLパターン・基点URL・設定例カテゴリ一覧は `references/url-map.md` を参照する。

## コマンドを調べる3経路

目的に応じて使い分ける。基本は A、足りなければ B、網羅が要るとき C。

### 経路A: 特定コマンドの検索（最頻・最速）

コマンド名がわかっているとき。サイト内検索でリーフURLを特定し、fetch する。

```
web_search:  site:rtpro.yamaha.co.jp <コマンド名やキーワード>
  例) site:rtpro.yamaha.co.jp ipsec ike encryption
  例) site:rtpro.yamaha.co.jp/RT/manual/rt-common nat descriptor type
```

ヒットした `.../<category>/<command>.html` を fetch する。系統別にパスを読み替える。
スイッチは `<model>/cmdref/...`、無線APは `<model>/<category>/...`（いずれも機種別。
検索結果の実URLをそのまま使う）。

### 経路B: カテゴリ単位で見渡す

各カテゴリには章ページ `<category>/<category>_chapter.html` があり、章内の全コマンドの
リーフURLが列挙されている。章ページを fetch して目的のリーフURLを拾い、fetch する。
リーフ末尾の「親トピック」リンクから章ページへ遡れる。

### 経路C: 全文PDFで網羅・横断確認

frameset を完全に回避できる。目次から該当章を読む。トークン消費が大きいので、全文を要約せず
必要箇所のみ読む。

- ルーター: `https://www.rtpro.yamaha.co.jp/RT/manual/rt-common/Cmdref.pdf`
- 無線AP:   `https://www.rtpro.yamaha.co.jp/RT/manual/wlx-common/Cmdref.pdf`
           （または機種別 `RT/manual/<model>/Cmdref.pdf`、例 `wlx402`, `wlx313`）
- スイッチ: `https://www.rtpro.yamaha.co.jp/RT/manual/<model>/Cmdref.pdf`（例 `swx2310p`）

旧ファーム向けは `rt-common-old/Cmdref.pdf`、特定リビジョンは
`archive/RT/manual/Rev.<x.xx.xx>/Cmdref.pdf` にある。

カテゴリのスラッグは英語トピック名（例 `mobile_internet`, `nat`, `ipsec`, `filter`,
`framerelay`, `usb`）。確証なくURLを組み立てない。不明なら経路A（検索）か経路CのPDF目次で確定する。

## リーフページの読み方

リーフページは次の見出しで構成される。この粒度で正確に引く。

- [書式] コマンド構文
- [設定値及び初期値] 各パラメーターの取り得る値と初期値（初期値は必ず確認する）
- [説明] 動作・関連コマンドへの注意
- [ノート] 補足・制約
- [設定例] YAMAHA 掲載の記述例
- [適用モデル] このコマンドが使える機種の列挙（対象機種が含まれるか必ず照合する）
- 親トピック 章ページへのリンク

適用モデルの照合は必須。特に `rt-common`（ルーター共通）は全機種混在なので、対象機種
（例 RTX830）が適用モデルに無いコマンドを案内しない。機種別リファレンス（スイッチ・無線AP）でも、
ファーム差で使えない場合があるため適用モデルや対応リビジョンを確認する。

## 設定例集（network.yamaha.com/setting）

実構成のサンプル config を探すときはこちら。通常HTMLで frameset の問題はない。

- 基点: `https://network.yamaha.com/setting`
- カテゴリ別一覧: `https://network.yamaha.com/setting/<category>/<topic>`
- 各一覧ページは「設定例タイトル＋使用機種＋リンク」の集合。使用機種で対象機種に合うものを選ぶ。
  個別ページは `.../setting/<category>/<topic>/.../<example>` 形式。

主なカテゴリ（詳細は `references/url-map.md`）:

- ルーター/FW: `router_firewall/`（`vpn`, `ipv6`, `internet`, `security`, `ts_router` ほか）
- UTM: `utm_appliance/`
- 無線LAN: `wireless_lan/`（`airlink`, `rt_coop`, `ts_wireless` ほか）
- スイッチ: `switch/`（`reliability`, `ip_routing`, `security`, `traffic_control` ほか）
- 仮想ルーター: `virtual_router/`（`aws`, `vrx_oam`）

## 標準ワークフロー

1. 対象機種を確定し、3系統のどれかを判定して参照基点（rt-common / `<model>/cmdref` / 機種別）を決める。
2. 目的を判定する。コマンド仕様か、設定例か。
   - コマンド仕様: 経路A（検索）でリーフを取得。広く見るなら経路B/C。
   - 設定例: `network.yamaha.com/setting/...` の該当カテゴリを fetch。
3. 取得した一次情報で裏取りする。リーフなら適用モデルを照合し、初期値を確認する。
4. 出典URLを併記して回答する（下記）。
5. ファーム・リビジョン依存の挙動は、必要なら該当リビジョンの PDF やリリースノートで確認する。

## 出典の明記

YAMAHA のページを参照したら、引用・要約した内容に対して、参照したページの正確なURLを併記する。
コマンド仕様はリーフページURL、設定例は個別設定例ページURLを示す。frameset の index ではなく、
実際に本文を取得したURLを出す。「YAMAHA より」だけでURLを省略しない。

## よくある落とし穴

- index.html を fetch して「情報が無い」と誤判断する。frameset なのでリーフ/PDF を使う。
- 機種非対応のコマンドを案内する。適用モデル欄を必ず照合する。
- 初期値の取り違え。「設定値及び初期値」を読まず説明文だけで判断しない。
- 系統の取り違え。スイッチを rt-common で探すなど。SWX は機種別 `cmdref`。
- カテゴリスラッグの当て推量。外すと404。検索かPDF目次で確定する。
- 新旧リビジョン差。古い機種/ファームは `rt-common-old` や `archive/.../Rev.*` を見る。
- 他社CLIの知識で代用する。ヤマハ独自構文。一次情報以外で確定しない。
