<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>

# AIペア型UI/UXテストツール：競合分析と新規プロダクト企画

日下様の要件（テスト設計書・ケース一覧に基づき、AIと同じ画面を見ながら状態遷移・配置・色味を一つずつ確認し、最終的にテスト結果書とエビデンスを成果物として残す）を軸に、既存製品を再調査し、ギャップが大きいと判断したため、ゼロベース開発を前提とした競合分析と企画書を以下にまとめます。

## 要件の再確認

必要な機能は次の5点に整理できます。第一に、テスト設計書・テストケース一覧のAI生成または取り込みです。第二に、AIと人間が同じ画面をリアルタイムに操作しながら確認する共同操作体験です。第三に、画面状態・ボタン配置・色味といった見た目の細部までの逐次チェックです。第四に、状態遷移を網羅的に辿る進行管理です。第五に、実行完了後にテスト結果書とスクリーンショット・ログなどのエビデンスを保管する成果物生成です。[^1][^2][^3][^4][^5][^6][^7][^8]

## 競合他社分析

主要8製品を、要件の5軸（設計書からのケース生成、AIとの共同操作性、視覚的差異検出、状態遷移網羅、結果書＋エビデンス成果物）で評価しました。


| ツール | 設計書→ケース生成 | AI共同操作 | 視覚差分検出 | 状態遷移網羅 | 結果書＋証跡 | 総合評価 |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |
| **TestCollab** | 要件・Jira・URL・スクショから生成、承認フロー付き[^9] | 弱い（管理中心） | 限定的 | 手動管理ベース | 実行ごとの記録は残るが監査特化ではない | 管理系では強いが「共同操作」の体験がない |
| **Katalon** | Jira要件からAIがテストケース・ステップを自動生成、要レビュー[^1] | 中（要件承認は人、実行はスクリプト/AI混在） | ある程度対応 | 対応 | プラットフォーム内でレポート化 | エンタープライズ機能は豊富だが操作は開発者視点 |
| **mabl** | 自然言語・Jira参照でテスト生成を10倍高速化[^10] | 弱い（人はレビューのみ、実行はエージェントが自律） | ビジュアルリグレッション監視あり[^10] | 継続実行でカバー | ダッシュボードでカバレッジ・品質スコア可視化[^11] | 「AIに委ねる」設計で、人と画面を一緒に見る用途とは方向性が違う |
| **QA.tech** | チャットでテスト意図から生成、PRごとに自動生成[^12][^2] | チャット型、人はレビューが中心 | 明記弱い | エージェントが探索的に網羅[^2] | PRレビューへの投稿あり | 開発フロー統合は強いが、逐一の目視確認向けではない |
| **Applitools Eyes** | なし（視覚テストAPI中心） | なし | AIによる人間の目に近い視覚差分検出が強力[^5][^6] | なし | スクリーンショット比較結果はあるが結果書形式ではない | 視覚差分検出は業界トップだが単機能 |
| **MagicPod** | Autopilotで自然言語からテスト作成・編集、AIアサーションで結果確認[^13][^14] | 中（自然言語操作は可能、リアルタイム共同操作ではない） | 画像差分確認ステップあり[^15] | ノーコードで管理可能 | 実行結果は蓄積されるが体系的な結果書生成は限定的 | 日本語対応・料金透明性は高いが「AIと並走する体験」は薄い |
| **Autify** | 個別見積り、詳細非公開[^16] | 不明（要問い合わせ） | 対応との情報あり | 情報限定 | 情報限定 | 情報開示が少なく比較が困難 |
| **testRigor** | 平易な英語でE2Eテスト記述[^17] | 弱い（記述型） | 限定的 | スクリプト網羅 | 実行ログは残る | 料金はシンプルだが共同操作体験なし |

この整理から見えるのは、**「AIがテストを自律的に作成・実行・修復する」方向（mabl、QA.tech）**と**「人がAIの支援を受けてケースを整備・実行する」方向（TestCollab、Katalon、MagicPod）**の二極に市場が分かれている点です。いずれも、日下様が求める「AIと画面を一緒に見ながら、状態やボタン配置、色味を逐一確認する」という**リアルタイム共同レビュー体験**を主軸に据えた製品は見当たりません。視覚差分検出ではApplitoolsが強いものの単機能であり、証跡管理ではZerocheckのようなコミット紐づき記録がある程度は近いですが、テスト設計書起点の運用や結果書生成とは別カテゴリです。[^10][^12][^13][^6][^7][^1]

## ギャップ分析

既存製品の多くはAIに実行を「委任」する設計であり、AIが自律的にテストを実行して失敗だけを人に報告する流れが主流です。これは効率的ですが、UI/UXの細部（配色、余白、ボタンの視認性など）の**主観的な品質判断**をAIと対話しながら人間が確認するには不向きです。加えて、テスト設計書ベースの進行管理と、成果物としての結果書・エビデンス保管を統合的に扱う製品は少なく、Jira連携やレポート機能はあっても、「テスト設計書の項目を1件ずつAIと確認し、完了したら証跡付きの結果書が自動的にできる」という一体化された体験は存在しません。この「共同レビュー＋進行管理＋成果物生成」の三点セットが市場の空白であり、ゼロベース開発の妥当性を支えています。[^18][^9][^10][^1]

## 新規プロダクト企画書

### コンセプト

テスト設計書・テストケース一覧を起点に、AIと人間が同じブラウザ画面をリアルタイムに共有しながら、画面状態・配置・色味・機能を1件ずつ確認し、全項目完了時に結果書とエビデンスを自動生成するSaaSです。既存の「AIに全自動で任せる」型（mabl、QA.tech）とも、「テスト管理が中心」型（TestCollab、Katalon）とも異なり、**人間の目とAIの支援を等しく重視するペア・レビュー型**を差別化軸とします。[^12][^9][^10]

### 主要機能

- **テスト設計書インポート／AI生成**：Excel、Word、Jira、Markdownからのテストケース取り込みと、画面URLやFigmaリンクからのAIケース草案生成（Katalonの要件→ケース生成の発想を発展）。[^1]
- **共同ブラウザセッション**：人間とAIが同じ画面をライブで操作し、AIが状態遷移や要素配置の観察結果をチャットで提示、人間が承認・修正・コメントを付与する対話型レビュー(QA.techのチャット型実行を、監視ではなく「並走」に転換)。[^2]
- **視覚チェックアシスト**：Applitools型のAI視覚差分検出を内包し、色味・レイアウトのズレをピクセル単位でなく人の目に近い基準で提示。[^5][^6]
- **進行トラッカー**：テストケース一覧に対する完了率、未確認の状態遷移パスをカンバン形式で可視化。
- **結果書＋エビデンス自動生成**：完了時にスクリーンショット、操作ログ、AIコメント、承認履歴を統合したPDF/Markdown形式の結果書を自動出力（Zerocheckのコミット紐づき証跡の発想を援用）。[^7]
- **CI/CD連携**：GitHub Actions、Playwrightとの接続で、既存の自動化資産を活かした半自動運用（TestCollabの自動化連携方針を参照）。[^9]


### 差別化ポイント

既存製品が「AIに委任する自動化」または「テスト管理の効率化」に主眼を置く中、本プロダクトは**AIを検査の相棒として画面上に常駐させる**ことで、手動UI/UXレビューの質を落とさずに速度を上げる立ち位置を取ります。これは日下様が重視する「やり直しの少ない高品質な確認プロセス」と直接一致します。

### 想定ユーザーと価格感

B2B SaaSのQA担当者、開発者兼QA、小〜中規模チームを主要ターゲットとし、MagicPodのクレジット制やテスト実行数に応じた課金モデルを参考に、月額固定＋AIレビュー回数に応じた従量制のハイブリッドプランが妥当です。[^13][^14]

### ロードマップ（案）

1. MVP：テストケース一覧の取り込み、共同ブラウザセッション、スクリーンショット付き結果書の3機能に限定してリリース。
2. 拡張：視覚差分AI、状態遷移トラッカー、Jira/GitHub連携を追加。
3. スケール：マルチユーザーの並行レビュー、多言語対応、SOC2などの認証取得（mablのSOC2 Type II取得を参考）。[^11]

## プロダクト名候補

| 候補名 | コンセプトとの整合性 | メモ |
| :-- | :-- | :-- |
| **Kensho（検証）** | 「検証」を英語表記にした和製グローバル名。AIとの厳密な確認作業を直感的に表す。 | ドメイン確保のしやすさを要確認 |
| **PairQA** | 「AIと人間のペア」を明示。QAツールとして機能が一目で伝わる。 | 汎用的すぎる可能性、差別化要素は訴求文で補強 |
| **ProofLoop** | 「証跡（Proof）」と「反復確認（Loop）」を組み合わせ、結果書・エビデンス生成という成果物指向を強調。 | 英語圏展開も見据えた名称 |
| **StateProof** | 「状態遷移の証明」を直接表現。機能訴求が強い分、汎用性はやや低い。 | B2B向けの機能訴求型ネーミング |
| **MiruQA（見るQA）** | 「見る」という視覚チェックの核心と「QA」を組み合わせた和製ネーミング。日本市場での親近感が高い。 | 海外展開時は別名併用を検討 |

総合的には、機能訴求と国際展開のバランスから **ProofLoop** または **PairQA** が候補の中心になりますが、日本市場先行かつ「見る」という行為を重視するなら **MiruQA** も有力です。最終選定にはドメイン・商標の空き状況の確認が必要です。
<span style="display:none">[^19][^20][^21][^22][^23][^24][^25][^26][^27][^28][^29][^30][^31][^32][^33]</span>

<div align="center">⁂</div>

[^1]: https://docs.katalon.com/katalon-platform/create-tests/generate-test-cases-with-ai

[^2]: https://docs.qa.tech/core-concepts/ai-agent-testing

[^3]: https://qa.tech/product

[^4]: https://forum.katalon.com/t/new-release-introducing-ai-powered-api-test-generation-in-katalon-studio/136347

[^5]: https://medium.com/@haridwar09/spot-every-pixel-how-applitools-is-revolutionizing-visual-testing-with-ai-a7c9c72c930c

[^6]: https://applitools.com/blog/why-screenshot-image-comparison-tools-fail/

[^7]: https://tryzerocheck.com/use-cases/soc2-evidence/

[^8]: https://beefed.ai/en/integrate-logs-screenshots-video-test-management

[^9]: https://testcollab.com/blog/ai-test-case-generation-tools

[^10]: https://www.mabl.com/ja/ai-test-automation

[^11]: https://www.mabl.com/solutions/software-technology

[^12]: https://qa.tech/

[^13]: https://magicpod.com/

[^14]: https://prtimes.jp/main/html/rd/p/000000059.000027392.html

[^15]: https://www.itreview.jp/products/magicpod/price

[^16]: https://autify.jp/pricing

[^17]: https://www.youtube.com/watch?v=nS-5bSxqp4k

[^18]: https://www.mabl.com/ai-test-automation

[^19]: https://www.mabl.com/ja/videos/agentic-testing-with-generative-ai

[^20]: https://docs.katalon.com/katalon-platform/katalon-ai-assistant

[^21]: https://docs-dev.katalon.com/katalon-studio/create-test-cases/generate-api-tests-with-ai-beta

[^22]: https://www.mabl.com/ai-application-testing

[^23]: https://www.mabl.com/auto-healing-tests

[^24]: https://help.mabl.com/hc/en-us/articles/31649455424660-Create-tests-with-generative-AI

[^25]: https://magicpod.com/pricing/

[^26]: https://applitools.com/blog/how-to-do-image-comparison-right/

[^27]: https://www.youtube.com/watch?v=Bq4i3j8FjU0

[^28]: https://it-trend.jp/development_tools/16769/price

[^29]: https://applitools.com/automated-visual-testing-best-practices-guide/

[^30]: https://www.youtube.com/watch?v=wRrqtI3zVx4

[^31]: https://service.valtes.co.jp/t-dash/blog/tool_comparison_vol_001/

[^32]: https://applitools.com/platform/eyes/

[^33]: https://sp-edge.com/companies/804336

