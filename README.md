# AIWebUITester

> AIと人間が同じ画面を見ながら Web UI/UX を一件ずつ確認する「AIペア型」テストツール

[English README](README.en.md)

## 概要

既存の AI テストツールは「AI に実行を委任し、失敗だけ人が見る」方向に寄っています。AIWebUITester はその逆で、**AI を検査の相棒として画面の隣に常駐させ、人間の目とAIの分析を等しく使う**ペア・レビュー型を目指します。

- 規格書・設計書・ソースコードから AI が UI/UX テスト設計書・手順書を生成
- テストチャートに従って人間が操作し、操作はすべて記録(スクリーンショット / 操作ログ / ネットワーク)
- 気になった箇所はレビューモードに切り替えて直接コメント、仕様の疑問はその場で AI チャット
- 完了時にテスト結果書+エビデンス(PDF / HTML Devレポート / HAR / GIF / PNG)を自動生成

詳細な背景は [競合分析と企画書](docs/planning/PRODUCT_PLAN_COMPETITIVE_ANALYSIS.md)、ver1.0.0 の全体像は [コンセプトスケッチ](docs/planning/VER_1_0_0_CONCEPT_SKETCH.png) を参照してください。

## ステータス

**企画・基盤整備段階です。** アプリケーションコードはまだありません。ver1.0.0 のスコープと技術方針は [docs/REPO_POLICY.md](docs/REPO_POLICY.md) と [ADR-0001](docs/adr/0001-browser-embedding.md) に記録しています。

## 技術方針(予定)

- Tauri 2 + TypeScript(デスクトップアプリ)
- Playwright(ブラウザ操作・記録エンジン)— ver1.0.0 はサイドカー並走方式、Tauri 内埋め込みは spike で検証([ADR-0001](docs/adr/0001-browser-embedding.md))
- GitHub Flow + Conventional Commits + release-please

## 開発

コントリビューション手順は [CONTRIBUTING.md](CONTRIBUTING.md) を参照してください。

## ライセンス

[AGPL-3.0-or-later](LICENSE)

Copyright (c) 2026 Takenori Kusaka

ネットワーク越しに本ソフトウェアの機能を提供する場合も、AGPL §13 によりソースコードの提供義務が生じます。コードを含むコントリビュートには [CLA への同意](CONTRIBUTING.md#コントリビューターライセンス同意cla)が必要です。
