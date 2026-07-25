# AGENTS.md — AI エージェント向け共通ガイド

AI コーディングエージェント(Claude Code ほか)がこのリポジトリで作業する際の共通指針。ツール非依存の事実と規約のみを書く。Claude Code 固有の設定は [CLAUDE.md](CLAUDE.md) と `.claude/` を参照。

## プロダクトの本質

AIWebUITester は **AI と人間が同じ画面を見ながら Web UI/UX を一件ずつ確認する「AIペア型」テストツール**(Tauri 2 デスクトップアプリ)。「AI に実行を委任し失敗だけ人が見る」既存ツールの逆を行き、AI を検査の相棒として常駐させる。

- 背景・競合分析: [docs/planning/PRODUCT_PLAN_COMPETITIVE_ANALYSIS.md](docs/planning/PRODUCT_PLAN_COMPETITIVE_ANALYSIS.md)
- ver1.0.0 の全体像: [docs/planning/VER_1_0_0_CONCEPT_SKETCH.png](docs/planning/VER_1_0_0_CONCEPT_SKETCH.png)
- 運用方針の SSOT: [docs/REPO_POLICY.md](docs/REPO_POLICY.md)

## 現在のステータス(2026-07 時点)

**企画・基盤整備段階。アプリケーションコードは未着手(scaffold 前)。**
`create-tauri-app` による scaffold は独立したタスクとして行う。それまでの変更対象は docs / .github / 開発環境設定に限る。

## リポジトリ地図

| パス | 内容 |
|---|---|
| `docs/REPO_POLICY.md` | 運用方針の SSOT(公開範囲・ブランチ戦略・CI 方針) |
| `docs/adr/` | 技術決定記録。1決定1ファイル(`NNNN-*.md`) |
| `docs/planning/` | 企画書・コンセプトスケッチ(歴史資料。書き換えない) |
| `docs/github/` | GitHub 側設定の記録(Ruleset JSON 等) |
| `.github/workflows/` | CI(現在は gitleaks のみ。scaffold 後に lint/test/build を追加) |
| `src/` / `src-tauri/` | (予定)TS フロントエンド / Rust バックエンド。Tauri 標準構成 |

## 技術決定(要点)

- スタック(予定): Tauri 2 + TypeScript + Svelte 5 + Vite。package manager は **npm**([QuickScribe](https://github.com/Takenori-Kusaka/QuickScribe) の規約を踏襲)
- ブラウザ制御: **ver1.0.0 は Playwright サイドカー並走**。Tauri 内埋め込み(multiwebview)は `spike/embedded-webview` で検証([ADR-0001](docs/adr/0001-browser-embedding.md))
- 新しい技術決定は必ず `docs/adr/NNNN-*.md` に「なぜ」を残す

## 開発規約

- **ブランチ**: GitHub Flow。`main` への直 push は Ruleset で禁止(PR 必須・squash のみ・セルフマージ可)。作業は `feat/*` `fix/*` `docs/*` `chore/*`
- **コミット**: Conventional Commits(`feat:` `fix:` `docs:` `chore:` `test:` `refactor:`)。PR タイトルも同形式(squash タイトルになる)
- **リリース**: release-please(manifest 方式)。バージョンは手動で触らない
- **CI**: PR ゲートは CI green(現在は gitleaks)。scaffold 後は lint / test / build も必須化予定
- **GitHub 操作**: `gh` CLI を使う(PR 作成・CI 確認・issue 操作)

## 触ってはいけないもの

- `.env*`(秘密情報。読み取りも書き込みも不可。共有が必要な項目は `.env.example` へ)
- `docs/planning/` 配下(企画時点の記録として保存。更新は新ファイルで)
- `version.txt` / `.release-please-manifest.json`(release-please が管理)
- 生成物: `node_modules/` `dist/` `src-tauri/target/`

## 検証(「動いた」と言える条件)

- 現段階: PR 上の CI が green + `git status` が clean
- scaffold 後: `npm test`(Vitest)/ `npm run lint` / `npm run build` が全て green になってから PR を出す。UI 変更はスクリーンショット添付
