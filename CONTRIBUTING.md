# Contributing

現在は企画・基盤整備段階のため、Issue での提案・質問を歓迎します。コードのコントリビューション手順はアプリの scaffold 後に拡充します。

## 開発フロー

- **GitHub Flow**: `main` から作業ブランチを切り、Pull Request でマージします。`main` への直接 push は Ruleset で禁止しています
- **マージ方式**: squash マージのみ
- **コミット規約**: [Conventional Commits](https://www.conventionalcommits.org/ja/v1.0.0/)。squash マージのため **PR タイトル**が規約に従っていれば十分です(例: `feat: add review mode annotations`)
- **リリース**: [release-please](https://github.com/googleapis/release-please) が Conventional Commits からバージョンと CHANGELOG を自動生成します

## ブランチ名

`<type>/<short-description>` 形式を推奨します(例: `feat/review-mode`, `fix/har-export`, `docs/adr-0002`)。

## Issue / PR

- バグ報告・機能提案は [Issue forms](.github/ISSUE_TEMPLATE) から
- PR は [テンプレート](.github/pull_request_template.md) に従って、目的・変更内容・確認方法を記載してください
