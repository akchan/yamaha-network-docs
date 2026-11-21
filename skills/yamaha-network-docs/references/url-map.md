# URL マップ

2026-11-21 に `https://www.rtpro.yamaha.co.jp/RT/manual.html`（マニュアル配布ページ）で確認した内容。
機種や対応リビジョンが変わっていそうなら、このページを取得して確かめる。

## コマンドリファレンスの `<base>`

URL は `https://www.rtpro.yamaha.co.jp/RT/manual/<base>/`。どの `<base>` にも `cmdref_index.html`、`toc.html`、`Cmdref.pdf` がある（`rt-common-old` は PDF だけ）。

| 機種 | `<base>` |
|---|---|
| vRX、RTX840、RTX3510、RTX1300、RTX1220、RTX830、RTX1210、RTX5000、RTX3500 | `rt-common` |
| RTX3000、RTX1500、RTX1100、RTX1200、RTX810、RT250i、RT107e、SRT100 | `rt-common-old`（PDF のみ） |
| NVR700W、NVR510 | `nvr700w_nvr510` |
| NVR500 | `nvr500` |
| FWX120 | `fwx120` |
| NWR100 | `nwr100` |
| SWX3220（16MT/16TMs/30MC/30TCs） | `swx3220/cmdref` |
| SWX3200 | `swx3200/cmdref` |
| SWX3100 | `swx3100/cmdref` |
| SWX2320、SWX2322P | `swx2320/cmdref` |
| SWX2310 | `swx2310/cmdref` |
| SWX2310P | `swx2310p/cmdref` |
| SWX2300 | `swx2300/cmdref` |
| SWX2220、SWX2221P、SWX2220P | `swx2220/cmdref` |
| SWX2210 | `swx2210/cmdref` |
| SWX2210P | `swx2210p/cmdref` |
| WLX413、WLX333、WLX232、WLX323、WLX322、WLX222、WLX212 | `wlx-common` |
| WLX402 | `wlx402` |
| WLX313 | `wlx313` |
| WLX302 | `wlx302` |

PDF の `Cmdref.pdf` は `<base>` の直下にある（スイッチも `swx2320/Cmdref.pdf` で、`cmdref/` の下ではない）。
SWX2200/2110/2100 と UTX にはコマンドリファレンスがなく、ユーザーガイドだけがある。
特定リビジョンの旧版は `https://www.rtpro.yamaha.co.jp/archive/RT/manual/Rev.<x.xx.xx>/Cmdref.pdf` にある。

## 設定例集のカテゴリ

`https://network.yamaha.com/setting/<category>/<topic>`

- `router_firewall`: `vpn` `ipv6` `internet` `flets` `cloud` `security` `internet_phone` `monitor` `custom_gui` `multicast` `file_sharing` `other_operation` `switch_control` `ts_router`
- `switch`: `oam` `virtualization` `reliability` `ip_routing` `traffic_control` `security` `solutions`
- `wireless_lan`: `airlink` `rt_coop` `wireless_terminal` `yno` `ts_wireless`
- `utm_appliance`: `introduction_utm` `vpn_utm` `virtual_lan_utm`
- `virtual_router`: `aws` `vrx_oam`

## その他の入口

- マニュアル配布（ユーザーガイド、Web GUI マニュアル含む）: `https://www.rtpro.yamaha.co.jp/RT/manual.html`
- ルーターの技術資料: `https://www.rtpro.yamaha.co.jp/RT/docs/index.html`
- リリースノート: `https://www.rtpro.yamaha.co.jp/RT/docs/relnote/index.html`
- ファームウェア: `https://www.rtpro.yamaha.co.jp/RT/firmware/index.php`
- スイッチの技術情報: `https://www.rtpro.yamaha.co.jp/SW/document.html`
- 無線 AP の技術資料: `https://www.rtpro.yamaha.co.jp/AP/docs/<model>/index.html`（例 `wlx413`）
- 製品ごとの技術資料: `https://network.yamaha.com/products/routers/<model>/techdocs`
- 概念解説: `https://network.yamaha.com/knowledge/`
