# yamaha-network-docs

ヤマハネットワーク機器（RTX/NVR/vRX ルーター、SWX スイッチ、WLX 無線AP）の
YAMAHA のコマンドリファレンスと設定例集を、出典URL付きで参照・引用するための Claude Code スキルです。

コマンドの書式・初期値・適用モデルの確認、設定例の検索、config の読み書き・レビューに使えます。

## できること

- YAMAHA のコマンドリファレンスや技術資料、全文PDFから正確な情報を取得
- ルーター / スイッチ / 無線AP に応じて適切なページを選択
- 設定例集（`network.yamaha.com/setting`）から使用機種に合うサンプル config を提示
- 回答に出典URL を併記

## インストール

Claude Code 上で次を実行します。

```
/plugin marketplace add akchan/yamaha-network-docs
/plugin install yamaha-network-docs
```

インストール後、「ヤマハ」「RTX」「SWX」「WLX」「RTpro」「コマンドリファレンス」「設定例」
などの語が会話に出ると、スキルが自動的に参照されます。

> Web 取得を行うため、Claude Code 側で WebFetch / WebSearch 系ツールが使える環境が必要です。

## アップデート

```
/plugin marketplace update yamaha-network-docs
/reload-plugins
```

## アンインストール

```
/plugin uninstall yamaha-network-docs
```

## ライセンス

[MIT](./LICENSE) © 2026 akchan

## 免責

本スキルはヤマハ株式会社が提供・承認するものではなく、有志が作成した第三者ツールです。
同社とは無関係であり、参照先の YAMAHA ドキュメントの内容・可用性について保証しません。実機への適用前に必ず YAMAHA のドキュメントと適用モデルをご確認ください。
