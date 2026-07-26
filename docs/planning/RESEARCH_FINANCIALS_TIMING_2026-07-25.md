# 財務図表（損益分岐・ユニットエコノミクス・価格モデル）はプロセスのどの段階で入れるべきか

日付: 2026-07-25
背景: 本プロダクト（B2B SaaS想定）を個人開発でDay 0から開始するにあたり、「損益分岐グラフ等の財務図表はいつ描くべきか」を一次情報ベースで調査した。

---

## 結論（先に一行で）

**「金勘定をやるか/やらないか」ではなく「どの粒度の金勘定をいつやるか」が正しい問いである。**
主要方法論のコンセンサスは明確:

- **Day 1にやるべき**: ナプキン計算レベルの「実現可能性のケタ確認」= Minimum Success Criteria（MSC）1行 + フェルミ推定5〜10分。これはLean Canvasの一部（Revenue Streams / Cost Structure）であり、コーチの推奨と矛盾しない。
- **まだやるべきでない**: 詳細財務モデル、月次損益分岐グラフ、実測ベースのLTV/CAC、精緻な価格最適化。これらは実データ（顧客・チャーン・獲得コスト）が存在して初めて意味を持ち、Day 0では「creative writing（創作）」になる。

---

## 1. Ash Maurya（Running Lean / Lean Canvas / Scaling Lean）— 「5分のフェルミ推定はDay 1、詳細モデルは不要」

最も本件に直接的な出典。Maurya自身が **「ビルドの前に、ざっくり計算（back-of-the-envelope）で事業モデルの成立可能性をストレステストせよ」** と明言している。

- **Running Lean 第3版のプロセス順序**: ① Lean Canvasでアイデアを分解 → ② **Desirability / Viability / Feasibility のストレステスト（ここにフェルミ推定が入る）** → ③ 顧客インタビューで検証。つまり **簡易な金勘定はインタビューより前（=今日）** に位置づけられている。
  - 出典: [Running Lean, 3rd Edition, Ch.4 "Stress Test Your Idea for Feasibility"](https://www.oreilly.com/library/view/running-lean-3rd/9781098108762/ch04.html) / [O'Reilly 書籍ページ](https://www.oreilly.com/library/view/running-lean-3rd/9781098108762/)
- **5分ラピッド・バイアビリティ・テスト**（Mauryaのニュースレター, 2025-07-17）:
  1. **Goal Sizing**: 3年後のMinimum Success Criteria（最小成功基準）を1行で決める（例: 3年で年商$10M、個人開発なら「月商100万円で食える」等、自分の基準でよい）
  2. **Customer Sizing**: 顧客1社あたり年間売上をフェルミ推定（丸めた数字でよい）
  3. **Market Sizing**: MSC ÷ 顧客単価 = 必要顧客数。その数を市場が支えられるか確認
  - タイミングについて: **「Perform this test before building. 90% of founders waste 6-18 months developing products because they skip this validation step.」**「Before you ask 'Can I build this?' you need to ask 'Should I build this?'」
  - 価格の重要性の例: 開発者に$50/月で売ると1万顧客必要 → 建築士に$5,000/案件に変えると200顧客で成立。**技術は同じでも価格モデルで成立可否が変わる** — だからこそ価格の「仮説」はDay 1に置く価値がある。
  - 出典: [The 5-Minute Test That Validates Any Business Model (LEANFoundry newsletter)](https://www.leanfoundry.com/lean-1-2-3/jul-17-2025)
- **MSCの定義**: 「Your minimum success criteria is the smallest outcome that would deem the project a success X years from now (X ≤ 3)」。1%市場シェアのような希望的観測ではなく、タイムボックスした最小基準から逆算する。数字が合わないアイデアは早期に捨てるか、価格・顧客セグメントをピボットする。
  - 出典: [How to Test Whether Your Business Model is Worth Pursuing (Maurya, Medium)](https://medium.com/lean-stack/how-to-test-whether-your-business-model-is-worth-pursuing-c728af971f06) — パリの起業家の例: 簡単な割り算で「国内に存在しない4万人/年の顧客が必要」と判明し、数ヶ月の開発を節約した。
- **Scaling Lean**: 「5分のフェルミ推定でTraction Model（顧客スループットを10x刻みで積み上げる牽引モデル）をつくる」。詳細な財務予測（スプレッドシート）ではなく **顧客数ベースの粗いモデル** を推奨。
  - 出典: [Scaling Lean 抜粋PDF (InfoQ)](https://res.infoq.com/articles/scaling-lean-ash-maurya/en/resources/Scaling-Lean%20Excerpt.pdf) / [The New Book Unveiled: Scaling Lean (Medium)](https://medium.com/lean-stack/the-new-book-unveiled-scaling-lean-b7a1a03c68f2)
- 一方でMauryaは事業計画書型の詳細財務予測を明確に否定: [It's Time to Fire the Business Plan for Good (LEANFoundry)](https://www.leanfoundry.com/articles/fire-the-business-plan)

**要約: コーチの推奨（Lean Canvas先行）はMaurya流と一致。ただしMaurya流を正しくやるなら、Canvasと同日に「MSC 1行 + フェルミ推定5分」も含まれる。損益分岐「グラフ」はこの段階の道具ではない。**

## 2. Steve Blank / Eric Ries — 「PMF前の詳細財務予測は創作文」

- Steve Blank: **「No business plan survives first contact with customers.」**「Unless you have tested the assumptions in your business model first, outside the building, your business plan is just creative writing.」スタートアップは「未知の顧客ニーズ・未知の機能・スケール可能なビジネスモデルの探索組織」であり、既知を実行する大企業向けの5年財務計画は不適合。静的な財務予測ではなく、動的なビジネスモデル（仮説群）を検証せよ。
  - 出典: [No Business Plan Survives First Contact With Customers (steveblank.com)](https://steveblank.com/2014/10/14/no-business-plan-survives-first-contact-with-customers-2-minutes-to-see-why/) / [No One Wins In Business Plan Competitions (steveblank.com)](https://steveblank.com/2010/05/17/no-one-wins-in-business-plan-competitions/)
- Eric Ries: 検証前の大規模予測に基づく先行投資（インフラ・採用）で失敗した企業例を挙げ、**virtual metrics（虚栄の指標）や希望的予測ではなく actionable metrics（因果が分かる指標）** を要求。PMF前の精緻なforecastは意思決定に使えない。
  - 出典: [The Lean Startup (Amazon)](https://www.amazon.com/Lean-Startup-Entrepreneurs-Continuous-Innovation/dp/0307887898) / [Vanity Metrics (TechCrunch, Ries寄稿)](https://techcrunch.com/2011/07/30/vanity-metrics/)

**要約: 「損益分岐グラフを先に描く」のは検証前の仮定の上に仮定を積む行為で、Blank/Ries系では明確にアンチパターン。**

## 3. YC（Michael Seibel / Kevin Hale）— 「ユニットエコノミクスが効くのはスケール判断時。ただし価格仮説は最初から持て」

- Michael Seibel / YC Essential Startup Advice: 「unit economics really matter」だが文脈は**スケールの可否判断**。「If you have an unprofitable product, growth merely drains cash」「PMF前に成長させる意味はない」— つまり実測ユニットエコノミクスは **ユーザー・売上データが出てから** の規律。
  - 出典: [YC's Essential Startup Advice](https://www.ycombinator.com/library/4D-yc-s-essential-startup-advice) / [michaelseibel.com](https://www.michaelseibel.com/blog/yc-s-essential-startup-advice)
- Kevin Hale (Startup Pricing 101): 初期段階の顧客はアーリーアダプターで**価格感応度が低い**。安すぎる価格はむしろ信頼を損なう。初期の価格は「最適化」ではなく「仮説として置いて課金してみる」もの。精緻な価格モデル図は不要だが、**値付けの仮説はDay 1から持つべき**（インタビューで支払意思を聞くためにも必要）。
  - 出典: [Startup Pricing 101 (YC Library)](https://ycombinator.com/library/6h-startup-pricing-101) / [YouTube](https://www.youtube.com/watch?v=jwXlo9gy_k4)

## 4. SaaS実務: LTV/CACはいつ「測れる」ようになるか — 「初期のLTV/CACは指標ではなく仮定」

- Tomasz Tunguz（元Redpoint VC）: **「LTV/CAC is often meaningless for early stage startups」**。SaaSのチャーンは年10%以下が普通で、顧客ライフタイムの推定には3〜5年分のデータが要る。創業1〜3年でも正確に出せない。初期は代わりに **CAC Payback Period（回収期間）** を使え（14〜18ヶ月で実データが揃う）。
  - 出典: [The False Confidence of the LTV/CAC Ratio for Early Stage SaaS Startups (tomtunguz.com)](https://tomtunguz.com/challenge-of-cac-ltv/)
- 実務系の補足: 「If you have less than 12 months of data, your LTV calculation is an assumption, not a metric」。$5M ARR未満はpayback period優先、先行指標（90日リテンション等）を見よ。
  - 出典: [Burkland: LTV:CAC An Important (But Often Misunderstood) SaaS Metric](https://burklandassociates.com/2024/01/02/ltvcac-an-important-but-often-misunderstood-saas-metric/) / [Spike AI: SaaS LTV Explained](https://getspike.ai/blog/saas-ltv-calculation-formulas-benchmarks/)

**要約: Day 0のLTV/CACチャートは全項が仮定の掛け算であり「精密風の創作」。書くならフェルミ推定の1行（想定単価×想定継続年数 vs 想定獲得コストのケタ比較）で十分。**

## 5. 「早期のナプキン損益分岐」を支持する側 — ただし粒度が違う

早期の金勘定を支持する信頼できる論者（Maurya本人が筆頭）も、支持しているのは**「市場がそもそも成立するかのケタ確認」**であって損益分岐グラフではない:

- Maurya: 5分フェルミ推定・MSC・Traction Model（上記1）— 「数分で済む計算を省くから6-18ヶ月無駄にする」
- Kevin Hale: 価格仮説を最初から持つ（上記3）
- 区別の基準:
  - **ナプキン算（数分・Day 1にやる価値大）**: MSC、必要顧客数、想定単価、市場に何社いるか、ソロでも回るか（例: 月5万円×20社=月商100万円。日本のB2B devツール市場に20社は居るか？ 獲得チャネルは？）
  - **財務モデリング（数日〜数週・時期尚早）**: 月次P&L、損益分岐チャート、コホート別LTV/CAC、価格弾力性分析、3〜5年予測スプレッドシート

---

## ボトムライン: 今日やるべき最小の金勘定 vs まだやらないもの

### 今日（Day 0〜1）やるべき — 合計15分以内
1. **MSC 1行**: 「X年後に年商/月商いくらなら続ける価値があるか」を自分基準で1行書く（例: 2年後に月商100万円）
2. **フェルミ推定5〜10分**: MSC ÷ 想定単価 = 必要顧客数。その数の顧客が到達可能なチャネルに存在するか？ 単価の桁（月5千円か5万円か50万円か）で成立可否が変わるなら、それ自体がインタビューで検証すべき最重要仮説
3. **Lean CanvasのRevenue Streams / Cost Structure欄を仮説で埋める**（Canvasは元々金勘定の箱を含む — コーチ案とは対立ではなく包含関係）
4. 数字が合わなければ、コードを書く前に価格/セグメントをピボット（Mauryaの$50/月→$5,000/案件の例）

### まだやるべきでないもの（データが出るまで保留）
- 損益分岐グラフ・月次P&L・3〜5年財務予測（Blank: 「creative writing」）
- 実測LTV/CAC・チャーン前提の計算（Tunguz: 12ヶ月未満のデータでは「仮定であって指標ではない」。最初の実務指標はCAC回収期間）
- 精緻な価格最適化（Hale: 初期は価格仮説を置いて課金し、反応で学ぶ）

