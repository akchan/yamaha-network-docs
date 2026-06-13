# yamaha-network-docs

ヤマハネットワーク機器（**RTX/NVR/vRX** ルーター、**SWX** スイッチ、**WLX** 無線AP）の
公式コマンドリファレンスと設定例集を、**出典URL付き**で参照・引用するための Claude Code スキルです。

AI が記憶や他社機器（Cisco/Juniper 等）の知識でヤマハのコマンドを推測してしまう問題を避け、
必ず公式の一次情報（`rtpro.yamaha.co.jp` / `network.yamaha.com`）を取得して裏取りさせます。
コマンドの書式・初期値・適用モデルの確認、設定例の検索、config の読み書き・レビューに使えます。

## できること

- 公式コマンドリファレンスの **frameset の罠**（`index.html` が空になる問題）を回避し、
  リーフページ・章ページ・全文PDF から正確な情報を取得
- ルーター / スイッチ / 無線AP の **3系統で異なる参照先**を自動で判定
- コマンドの **適用モデル**照合と**初期値**確認を徹底
- 設定例集（`network.yamaha.com/setting`）から使用機種に合うサンプル config を提示
- 回答に**出典URL を併記**

## インストール

Claude Code 上で次を実行します。

```
/plugin marketplace add akchan/yamaha-network-docs
/plugin install yamaha-network-docs
```

インストール後、「ヤマハ」「RTX」「SWX」「WLX」「RTpro」「コマンドリファレンス」「設定例」
などの語が会話に出ると、スキルが自動的に参照されます。

> Web 取得を行うため、Claude Code 側で WebFetch / WebSearch 系ツールが使える環境が必要です。

## 構成

```
.
├── .claude-plugin/
│   ├── marketplace.json     # マーケットプレイス定義（このリポジトリ＝単一プラグイン配布）
│   └── plugin.json          # プラグイン定義
└── skills/
    └── yamaha-network-docs/
        ├── SKILL.md         # スキル本体（参照手順・ワークフロー）
        └── references/
            └── url-map.md   # 公式ドキュメントの詳細URLマップ
```

## ライセンス

[MIT](./LICENSE) © 2026 akchan

## 免責

本スキルは非公式です。ヤマハ株式会社とは無関係であり、参照先の公式ドキュメントの内容・
可用性について保証しません。実機への適用前に必ず公式ドキュメントと適用モデルをご確認ください。
