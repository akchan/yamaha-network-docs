# yamaha-network-docs

Claude Code ユーザー向けに、ヤマハネットワーク機器（RTX/NVR/vRX・SWX・WLX）の公式
ドキュメント参照スキルを「プラグイン」としてマーケットプレイス配布するためのリポジトリ。
このリポジトリは配布の器であり、機器設定の知識そのものはスキル本体（`SKILL.md`）が持つ。

## Language

**Marketplace**:
Claude Code が `/plugin marketplace add` で取り込む、配布の最上位カタログ。1つの Git
リポジトリ = 1つの Marketplace。このリポジトリは単一プラグイン専用の Marketplace。
_Avoid_: レジストリ、ストア

**Plugin**:
Marketplace に列挙され、ユーザーが `/plugin install` する配布単位。Skill・command・
agent・hook 等を内包しうる。本リポジトリの Plugin は Skill を1つだけ含む。
_Avoid_: パッケージ、拡張

**Skill**:
`SKILL.md`（frontmatter + 手順）で表現される、AI への手順・知識の注入単位。Plugin の
中身。本件の Skill は「ヤマハ公式ドキュメントを出典URL付きで参照する手順」。
_Avoid_: プロンプト、ツール

**正規名 (Canonical name)**:
repo = Marketplace = Plugin = Skill すべてに用いる単一トークン。`yamaha-network-docs`
（複数形）。ローカル作業フォルダのみ暫定で単数 `yamaha-network-doc`。
_Avoid_: yamaha-network-doc（単数。フォルダ名の名残）

## Flagged ambiguities

- **「ドキュメント」**: 2系統ある。(1) 配布物の説明文書（README 等）、(2) スキルが参照する
  ヤマハ公式ドキュメント。文脈で区別する。本 glossary の対象は主に (1)。

## 入れ子関係

Marketplace ⊃ Plugin ⊃ Skill。ユーザー導入は2段:
`/plugin marketplace add akchan/yamaha-network-docs` → `/plugin install yamaha-network-docs`。
