# CLAUDE.md — AIWebUITester

共通の事実・規約(プロダクト本質 / リポジトリ地図 / 開発規約 / 検証条件)は AGENTS.md にある。まずそちらに従う。

@AGENTS.md

以下は Claude Code 固有の指針のみ。

## コミュニケーション

- ユーザーへの応答は日本語。コードコメント・コミットメッセージは英語可。

## 現フェーズの作業境界(scaffold 前)

- アプリコードは存在しない。**scaffold(`create-tauri-app`)は明示依頼があるまで行わない。**
- 変更してよいのは docs / .github / 開発環境設定(このファイル・AGENTS.md・.claude/)のみ。
- 判断に迷ったら docs/REPO_POLICY.md → docs/adr/ の順に立ち返る。スコープを独断で広げない。

## コマンド(scaffold 後にここを確定させる)

package manager は **npm**(pnpm / yarn / bun は使わない)。scaffold 完了時に、実際の package.json に合わせて以下を確定記載し、CI のジョブと一致させること:

```text
npm ci            # install
npm run dev       # dev server (Tauri: npm run tauri dev)
npm test          # unit tests (Vitest) — 単体ファイルは npm test -- <path>
npm run lint      # ESLint
npm run format    # Prettier
npm run build     # production build
```

## 検証ループ(必ず回す)

1. 変更 → 現段階は `git status` clean + PR の CI(gitleaks)green を確認
2. scaffold 後は `npm test` / `npm run lint` / `npm run build` を green にしてから PR
3. 「動いた」はコマンドの exit code とスクリーンショットで示す。未検証を完了と言わない

## PR の作法

- `gh pr create` で PR #番号・CI 結果を確認できる形で作業する
- PR タイトル = Conventional Commits(squash タイトルになるため厳守)
- コミット末尾に `Co-Authored-By` トレーラを付与する

## メンテナンス方針

- このファイルと AGENTS.md は 200 行未満を保つ。「この行を消すと Claude が間違えるか」で取捨選択
- 強制が必要なルールは記述でなく `.claude/settings.json` の permissions / hooks に落とす
- scaffold 後の TODO: コマンド欄の確定 / Prettier の PostToolUse hook 追加 / `typescript-lsp` plugin 導入検討
