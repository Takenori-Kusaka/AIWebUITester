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

## ライセンス

本プロジェクトは **[AGPL-3.0-or-later](LICENSE)** で配布しています。コントリビュートされたコードも同ライセンスで公開されます。

## コントリビューターライセンス同意(CLA)

**コードを含む Pull Request を出す前に、本節に必ず同意してください。**

本プロジェクトは将来、企業向けに AGPL 以外の条件で提供する**デュアルライセンス**の選択肢を残しています。これはオーナーが全コードの著作権者である場合にのみ成立するため、外部コントリビュートには以下の同意が必要です。

Pull Request を提出することで、あなたは以下に同意したものとみなされます。

1. あなたは、提出する成果物(コード・ドキュメント・その他)を**自ら作成した**か、提出する正当な権利を有している
2. あなたは、提出した成果物について、プロジェクトオーナー(Takenori Kusaka)に対し、**AGPL-3.0 を含む任意のライセンス条件で利用・改変・再配布・サブライセンスする、取消不能・世界的・無償・非独占の権利**を許諾する(将来の商用ライセンス提供を含む)
3. あなたは、提出した成果物に対する自身の著作者人格権を、本プロジェクトの運営に必要な範囲で行使しない
4. 成果物は「現状のまま」提供され、あなたは明示・黙示のいかなる保証も行わない
5. **業務として、または雇用主の資産・時間・設備を用いて作成した成果物**を提出する場合は、事前に雇用主から許諾を得ていること(職務発明・職務著作の規程に該当しうるため)

### 同意の記録方法

PR 本文に次の1行を記載してください。

```
I have read and agree to the CLA in CONTRIBUTING.md.
```

あわせて、各コミットに `git commit -s` で `Signed-off-by:` トレーラーを付けてください([DCO](https://developercertificate.org/) と同形式)。

CLA に同意できない場合でも、**Issue での提案・バグ報告・議論は歓迎します**(これらに CLA は不要です)。
