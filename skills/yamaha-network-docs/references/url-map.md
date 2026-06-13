# URL マップ（ヤマハ公式ドキュメント）

SKILL.md から参照する詳細URL集。確認日時点で実在を確認したものは「確認済」と明記する。
カテゴリ名（スラッグ）の当て推量は避け、不明なものはサイト内検索かPDF目次で確定する。

## 目次

- [1. コマンドリファレンス（rtpro.yamaha.co.jp）](#1-コマンドリファレンスrtproyamahacojp)
- [2. リーフ／章ページの構造](#2-リーフ章ページの構造)
- [3. 全文PDF](#3-全文pdf)
- [4. 設定例集（network.yamaha.com/setting）](#4-設定例集networkyamahacomsetting)
- [5. 製品技術資料・その他](#5-製品技術資料その他)
- [6. 検索クエリの組み立て例](#6-検索クエリの組み立て例)

---

## 1. コマンドリファレンス（rtpro.yamaha.co.jp）

`http://` で案内されるが `https://` で fetch する。`index.html` は frameset で本文が取れない。

| 機器系統 | リファレンス基点（frameset。fetch しても空） | 備考 |
|---|---|---|
| ルーター RTX/NVR/vRX | `https://www.rtpro.yamaha.co.jp/RT/manual/rt-common/index.html` | 全機種共通。リーフも配下（確認済: frameset） |
| 旧ルーター/旧ファーム | `https://www.rtpro.yamaha.co.jp/RT/manual/rt-common-old/` | 旧リビジョン系（PDF 確認済） |
| 無線AP WLX（共通） | `https://www.rtpro.yamaha.co.jp/RT/manual/wlx-common/index.html` | 共通 frameset と PDF（確認済: frameset） |
| 無線AP WLX（機種別リーフ） | `https://www.rtpro.yamaha.co.jp/RT/manual/<model>/<category>/<command>.html` | リーフは機種別（例 `wlx302/airlink/airlink_ssid.html` 確認済） |
| スイッチ SWX（機種別） | `https://www.rtpro.yamaha.co.jp/RT/manual/<model>/cmdref/index.html` | `<model>` は型番小文字 |

スイッチの `<model>` 例（実在確認済）: `swx2310p`, `swx2310`。
無線APの `<model>` 例（実在確認済）: `wlx302`, `wlx313`, `wlx402`, `wlx212`, `wlx202`。
他機種も同形式だが、機種プレフィックスが変動するため、URLを組む前にサイト内検索（6章）で実在を確認する。
特に無線AP・スイッチはリーフが機種別なので、共通URLを当て推量しない。

上表の index.html は基点の所在を示すためのもので、本文取得には使わない。
本文は2章のリーフ／章ページか3章のPDFから取得する。

---

## 2. リーフ／章ページの構造

DITA 由来の静的HTMLで、リーフ／章ページは通常HTMLとして正しく取得できる（確認済）。

### リーフページ（個別コマンド）

```
https://www.rtpro.yamaha.co.jp/RT/manual/rt-common/<category>/<command>.html
```

- 例（確認済）: `.../rt-common/mobile_internet/execute_at-command.html`
- 見出し: [書式] [設定値及び初期値] [説明] [ノート] [設定例] [適用モデル]、および親トピック。
- 適用モデル欄に対象機種が含まれるか必ず照合する。初期値も必ず確認する。

### 章ページ（カテゴリ index）

```
https://www.rtpro.yamaha.co.jp/RT/manual/rt-common/<category>/<category>_chapter.html
```

- 例（確認済）: `.../rt-common/mobile_internet/mobile_internet_chapter.html`
- その章の全コマンドのリーフURLが列挙される。カテゴリを見渡すときの入口。
- リーフ末尾の「親トピック」からこの章ページへ遡れる。

### 確認済のカテゴリスラッグ（一部）

- ルーター `rt-common`: `mobile_internet`, `framerelay`, `usb`
- 無線AP（機種別）: `airlink`（例 `wlx302/airlink/airlink_ssid.html` 確認済）

これ以外（`nat`, `ipsec`, `filter`, `ip`, `ipv6`, `dhcp`, `dns`, `pp`, `tunnel`, `wireless` など）は
妥当だが未確認。URLを直書きせず、サイト内検索（6章）かPDF目次で正確なスラッグとファイル名を確定する。

無線AP・スイッチはリーフが機種別ディレクトリにあり、機種プレフィックスが変わる。
リーフURLの発見は経路A（検索）が最も確実。DITA構造（書式/設定値/適用モデルなど）と
全文PDF・章ページの考え方はルーターと共通。

---

## 3. 全文PDF（frameset 回避の確実手段）

| 対象 | URL | 状態 |
|---|---|---|
| ルーター（最新共通） | `https://www.rtpro.yamaha.co.jp/RT/manual/rt-common/Cmdref.pdf` | 確認済 |
| ルーター（旧共通） | `https://www.rtpro.yamaha.co.jp/RT/manual/rt-common-old/Cmdref.pdf` | 確認済 |
| ルーター（特定Rev.） | `https://www.rtpro.yamaha.co.jp/archive/RT/manual/Rev.<x.xx.xx>/Cmdref.pdf` | 確認済（例 Rev.9.00.01） |
| 無線AP（共通） | `https://www.rtpro.yamaha.co.jp/RT/manual/wlx-common/Cmdref.pdf` | 確認済 |
| 無線AP（機種別） | `https://www.rtpro.yamaha.co.jp/RT/manual/<model>/Cmdref.pdf` | 確認済（例 `wlx402`, `wlx313`） |
| スイッチ | `https://www.rtpro.yamaha.co.jp/RT/manual/<model>/Cmdref.pdf` | 確認済（例 `swx2310p`, `swx2310`） |

PDFは数百ページ規模。全文を読み込んで要約せず、目次から該当章のみ参照する。
1コマンドだけ必要なら、PDFより2章のリーフページの方が軽い。

---

## 4. 設定例集（network.yamaha.com/setting）

通常HTML（frameset なし、確認済）。基点は `https://network.yamaha.com/setting`。
各「カテゴリ/トピック」ページは、設定例タイトル・使用機種・個別ページへのリンクの一覧。
個別ページ形式は `.../setting/<category>/<topic>/.../<example>`。

### ルーター/ファイアウォール `router_firewall/`

`ts_router`(トラブルシューティング), `vpn`(インターネットVPN), `cloud`, `flets`,
`internet`, `ipv6`, `security`, `internet_phone`, `monitor`, `custom_gui`,
`multicast`, `file_sharing`, `other_operation`, `switch_control`

### UTM `utm_appliance/`

`introduction_utm`, `vpn_utm`, `virtual_lan_utm`

### 無線LANアクセスポイント `wireless_lan/`

`ts_wireless`, `airlink`(無線LAN接続設定), `rt_coop`(ルーターからの制御),
`wireless_terminal`, `yno`

### スイッチ `switch/`

`oam`(保守・運用), `virtualization`(仮想化), `reliability`(帯域確保・冗長化),
`ip_routing`(IPアドレス管理・ルーティング), `traffic_control`, `security`,
`solutions`(市場別設定例)

### 仮想ルーター `virtual_router/`

`vrx_oam`(運用・保守), `aws`(AWSを利用)

上記スラッグは設定例トップのナビから確認済。個別設定例ページのURL末尾は一覧ページ内のリンクから
取得する（推測しない）。各設定例の冒頭に「使用機種」が明記されるので、対象機種に対応する例を選ぶ。

---

## 5. 製品技術資料・その他

- 製品ごとの技術資料ハブ: `https://network.yamaha.com/products/routers/<model>/techdocs`
  （例 `rtx830`）。ここから当該機種のコマンドリファレンス（rt-common）などへ誘導される。
- ファームウェア配布: `http://www.rtpro.yamaha.co.jp/RT/firmware/index.php`
- リリースノート一覧: `http://www.rtpro.yamaha.co.jp/RT/docs/relnote/index.html`
- 取扱説明書一覧: `http://www.rtpro.yamaha.co.jp/RT/manual.html`
- 知識&技術（概念解説）: `https://network.yamaha.com/knowledge/`（`vpn`, `routing`,
  `qos`, `vlan`, `ipv6`, `wlan` など）

---

## 6. 検索クエリの組み立て例（経路A）

サイト内検索でリーフURLを最短特定する。

```
site:rtpro.yamaha.co.jp/RT/manual/rt-common  ipsec ike encryption
site:rtpro.yamaha.co.jp/RT/manual/rt-common  nat descriptor type
site:rtpro.yamaha.co.jp/RT/manual            airlink ssid
site:rtpro.yamaha.co.jp/RT/manual/swx2310p   vlan
site:network.yamaha.com/setting              IPsec 拠点間 RTX830
```

- ルーターは `rt-common` に絞ると精度が上がる。
- 無線AP・スイッチはリーフが機種別なので、機種が確定していればそのパス（例 `swx2310p`）に絞り、
  未確定なら `RT/manual` 全体で検索してヒットした機種別リーフを使う。
- ヒットした `.html`（リーフ）をそのまま fetch する。`index.html`（frameset）がヒットしたら
  本文は取れないので、近傍の章ページ／リーフを探すかPDFに切り替える。
