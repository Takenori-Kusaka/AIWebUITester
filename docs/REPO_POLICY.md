# REPO_POLICY — リポジトリ運用方針 (SSOT)

2026-07-25 の repo-setup ヒアリング(Buzz #repo-setup チャンネル)に基づく決定事項。以後のセットアップ・開発判断はこのファイルを根拠とする。変更は PR で行う。

## ヒアリング結果

| 項目 | 決定 |
|---|---|
| 公開範囲 | **public (OSS)**。経緯: 2026-07-25 に特許出願前の公知化回避のため一時 private 化 → 2026-07-26 オーナー決定で public に復帰(Buzz #1on1 スレッド)。**特許出願は個人では追わない**(費用対効果で棄却。事業化が見えた場合の法人出願のみ再検討)。防御力の方針 = 開発速度・独自データ・OSS ディストリビューション |
| プロジェクト種別 | デスクトップアプリ(Tauri 2 + TypeScript)。AIペア型 Web UI/UX テストツール |
| 目標 | コンセプトスケッチ([VER_1_0_0_CONCEPT_SKETCH.png](planning/VER_1_0_0_CONCEPT_SKETCH.png))の **ver1.0.0** |
| チーム | オーナー1名 + AI エージェント(Claude Code) |
| 参照実装 | [QuickScribe](https://github.com/Takenori-Kusaka/QuickScribe) の規約・構成を踏襲 |

## 運用ルール

- **ライセンス**: MIT
- **ブランチ戦略**: GitHub Flow。`main` への直接 push は Ruleset で禁止、PR 必須(ソロ開発のため必須レビュー数は 0 = セルフマージ可)
- **マージ**: squash のみ。PR タイトル = Conventional Commits
- **リリース**: release-please(manifest 方式、release-type: simple)。scaffold 後に node 用へ切替を検討
- **CI**: 1ワークフロー=1責務 / サードパーティ action は SHA ピン / `permissions` 最小(トップレベル `contents: read`)/ `concurrency` で旧実行キャンセル
- **Secrets**: 機密は GitHub Secrets、非機密は Variables。ローカルは `.env`(gitignore 済み)+ `.env.example`。gitleaks を CI で常時実行、GitHub 側で secret scanning + push protection 有効
- **フォルダ構成(予定)**: Tauri 標準(`src/` = TS フロントエンド、`src-tauri/` = Rust)。QuickScribe と同型

## 技術決定

- ブラウザ制御方式: [ADR-0001](adr/0001-browser-embedding.md) — ver1.0.0 は Playwright サイドカー並走、Tauri 内埋め込みは spike で検証
- 今後の技術決定は `docs/adr/NNNN-*.md` に追記する

## AI エージェント向けガイド

- `AGENTS.md` / `CLAUDE.md` は CC-EnvSetup が管理(2026-07-25 依頼済み)
