# Deep Research: 企画初期に描くべき「絵」の種類・順序・タイミング（2026-07-25）

**目的**: 本プロダクト（AIペア型UI/UXテストツール）の企画初期に「どの図を・どの順で描くべきか。ジャーニーマップやリーンキャンバスはもう書き始めるものか」への裏づけ調査。
**方法**: 並列deep research 2系統（①原典・提唱者の一次情報、②実務家・個人開発文脈）。

---

## 系統①: 原典（提唱者）ベースの調査結果

### Lean Canvas（Ash Maurya, "Running Lean"）
- 判断対象: Plan A（初期仮説）の文書化と「最もリスキーな仮説」の特定。事業計画書の代替。
- タイミング: **Day 1、顧客インタビューの前**。プロセスは ①Plan A文書化→②最リスク特定→③体系的検証。
- タイムボックス: **20分以内**（「タイマーをセットしてスナップショットを撮る。完璧を目指すな」）。
- 警告: 「1ページで説明できないなら複雑すぎる」「ソリューションの束縛はできるだけ遅く」。Canvasは計画書ではなく仮説ログ。
- 出典: https://ashmaurya.com/blog/what-is-lean-canvas

### Business Model Canvas / Value Proposition Canvas（Osterwalder）
- VPCはBMCの「Value Proposition×Customer Segment」2ブロックへのズームイン用プラグイン（2014 "Value Proposition Design"）。
- MauryaのLean CanvasはBMC改変（2010）。正典的位置づけ: Lean Canvas=不確実性の高い初期スタートアップ、BMC=既存事業のモデル記述。**Day 1にはどちらか一方**。
- 出典: https://www.strategyzer.com/library/achieve-product-market-fit-with-our-brand-new-value-proposition-designer-canvas

### Customer Journey Map（NN/g）
- 着手前の2大決定: Current-state vs Future-state ／ **Assumption-first vs Research-first**。
- **仮説ベース（assumption-first）はコンセプト段階で描いてよい**——実務家の62%がhypothesis-firstで開始。ただし「後続リサーチで検証する下書き」「必要なリサーチを特定するための出発点」という位置づけが条件。
- 推奨ハイブリッド: assumption-based現状マップ → リサーチ検証 → future-stateマップ。
- 警告: 「真実に基づけ（Base it on truth）」。リサーチを飛ばして視覚化に走ると「beautiful yet flawed」なマップになる。プロセス（協働）＞成果物。
- 出典: https://www.nngroup.com/articles/journey-mapping-approaches/ ／ https://www.nngroup.com/articles/journey-mapping-how/ ／ https://www.nngroup.com/articles/journey-mapping-101/

### User Story Mapping（Jeff Patton）
- 判断対象: 全体像からリリーススライス/MVP（walking skeleton）を切る判断＋shared understanding形成。
- タイミング: ディスカバリー段階・**ソリューション方向が定まった後、開発着手前**。前提=ユーザーと目標の仮説があること。
- 警告: 「共通理解は完璧なドキュメントよりはるかに重要」。カードは会話の想起装置。
- 出典: https://jpattonassociates.com/the-new-backlog/

### Impact Mapping（Gojko Adzic）
- 判断対象: Goal→Actor→Impact→Deliverableの因果でスコープ/ロードマップを判断。「非現実的なプロジェクトを高くつく前に止める」。
- タイミング: マイルストーン作業開始時。前提=測定可能なビジネスゴール。1〜2日WS。
- 出典: https://www.impactmapping.org/about.html

### 順序の正典
- **Double Diamond**（Design Council 2005）: Discover（想定でなく理解）→Define→Develop→Deliver。問題側が解決側に先行。 https://www.designcouncil.org.uk/resources/framework-for-innovation/
- **Cagan（SVPG）**: 成果物の順序でなく「4大リスク（Value/Usability/Feasibility/Viability）をプロダクションコード前に安価に潰す」。 https://www.svpg.com/four-big-risks/
- **Torres（Opportunity Solution Tree）**: 前提=①顧客と価値提案の理論 ②定義済みアウトカム ③**顧客インタビュー3〜4件**。「頭の中からオポチュニティをでっち上げると自分のバイアスを持ち込む」。ただし crummy first draft 精神で早く描き始めよ。 https://www.producttalk.org/opportunity-solution-trees/

### 原典合成の推奨シーケンス
1. Day 1（20分）: Lean Canvas【Maurya】
2. 同週: 仮説ベースJourney Map（半日・知識ギャップ特定用）【NN/g】／（事業ゴール明確なら）Impact Mapping【Adzic】
3. 顧客インタビュー3〜4件後: OST【Torres】・検証済みJourney Map【NN/g】
4. ソリューション方向確定後・開発前: User Story Mapping【Patton】
5. 全期間: 4リスクをプロトタイプで検証【Cagan】

**全著者共通の警告**: (1)成果物はスナップショット/仮説であり完成文書ではない (2)協働プロセス＞成果物（documentation theater の否定） (3)早すぎるソリューション固定の禁止。

---

## 系統②: 実務家・個人開発（ソロB2B SaaS）文脈の調査結果

### 選定原理
「最もリスキーな仮説を、最も安く検証できる成果物を先に作る」（RAT: Riskiest Assumption Test）。B2B QAツールの場合、経験豊富なエンジニアには実現性（feasibility）は低リスク→**最大リスクは需要（desirability）**。

### 推奨最小セット（順序つき）
| 順 | 成果物 | 工数 | 根拠 |
|---|---|---|---|
| 1 | 1枚のリーン仮説メモ（ICP・課題仮説・競合代替手段・最リスク仮説） | 半日 | Torres/Cagan「PRDはディスカバリーの代わりに書かれるのが問題」 |
| 2 | 顧客インタビュー10〜20件＋サマリー | 2〜4週 | Lenny/Todd Jackson「最重要のテスト」。Mom Test: 意見でなく過去の行動を聞く（「今どうやってUIテストしてる?」）。YCは毎週「何人と話したか」を問う |
| 3 | LP＋モック画面数枚（スモークテスト） | LP 2〜4時間 | 冷たいオーディエンスでCTR 2〜5%=強シグナル。事前販売（LOI）が最高EVの検証手段。LP先行組は初収益到達が約40%速い（Indie Hackers分析） |
| 4 | 仮説ベースジャーニーマップ（主要フロー1本のみ） | 1日 | NN/g 62%が仮説先行。「後続リサーチで検証する下書き」条件付き |
| 5 | 低忠実度プロトタイプ／ファットマーカースケッチ | 2〜5日 | Cagan「プロトタイプはMVPテクニックの最良」。Shape Up: 太マーカーで描けない詳細は描かない |

### まだ作るべきでないもの（premature）
- **PRD/詳細仕様書**: ディスカバリーの代替として書かれるのが典型的失敗（Cagan）
- **競合ポジショニング2x2**: Dunford本人が「PMF前はポジショニング作業の意味が薄い。15社入り競合マトリクスはデッキの中にしか存在しない」。今必要なのは「競合代替手段のリスト」だけ（手動テスト・Playwright自作・既存QAツール）
- **高忠実度モック/デザインシステム**: 詳細を早期に固めすぎる（Shape Up）
- **フル機能ロードマップ**: アウトカムでなく出力にコミットさせる（Cagan）
- **網羅的ペルソナ・フルサービスブループリント**: 検証済みリサーチが前提
- 失敗分析: ソロ失敗の主因は「検証前に作り始めて momentum 崩壊」。**64%は友人への確認を「検証」と誤認**（Indie Hackers 50件分析）

### 主要出典
- SVPG: https://www.svpg.com/discovery-vs-documentation/ ／ https://www.svpg.com/flavors-of-prototypes/
- Lenny's: https://www.lennysnewsletter.com/p/how-to-validate-your-b2b-startup ／ https://www.lennysnewsletter.com/p/validating-your-startup-idea
- YC: https://www.ycombinator.com/library/Iq-how-to-talk-to-users
- Shape Up: https://basecamp.com/shapeup/1.3-chapter-04
- Dunford: https://www.aprildunford.com/post/a-quickstart-guide-to-positioning
- Mom Test: https://frankthoughts.substack.com/p/the-mom-test-talking-to-customers
- Indie Hackers: https://www.indiehackers.com/post/i-analyzed-50-failed-solo-founder-projects-the-1-reason-wasnt-bad-ideas-it-was-execution-collapse-eb106b4a2b

