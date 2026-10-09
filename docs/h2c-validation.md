# Phase H2c — 完了・検証記録

ローカルstaging内のH2b修正2件とPages design foundationを完了。静的検証29項目PASS、初期browser表示確認PASS。Git / GitHub / Pages公開操作は実施していない。

## 完了報告（30項目）

| # | 項目 | 結果 |
|---|---|---|
| 1 | Working directory | 指定のwan-animate2-apple-silicon-lab stagingを確認し、ここだけを編集 |
| 2 | H2b fix 1 | README ModelsにComfy-Org / ComfyUI distributionであること、upstream originalとbyte-identicalとは主張しない旨を1段落追加 |
| 3 | H2b fix 2 | v3 reference SHA、v4 pose_endをfixed_variablesから分離 |
| 4 | Schema | schema_version=1を維持。v3/v4にbaseline_experiment_id=ANIMATE2-V2、run_conditionsを追加。v3 changed referenceにbefore/after SHA、v4命名情報はartifact_identificationへ |
| 5 | Existing integrity | 既存21ファイル中変更は2件のみ。他19件、workflow、結果、数値、SHA、status、chronologyは維持 |
| 6 | Site path | staging内site/index.html |
| 7 | Site tree | 下記。site計24ファイル |
| 8 | Site total bytes | 261,986 bytes。HTML 29,753 bytes、CSS 19,698 bytesを含む |
| 9 | Concept | Dark editorial technical field report。TECHNICAL PASS ≠ VISUAL SUCCESSを中心メッセージに設定 |
| 10 | Brand relationship | main Showcaseのローカル実装からcharcoal/navy・green・cyan・mono・large type・thin gridを継承し、研究/telemetry主体へ再構成 |
| 11 | Hero | WAN ANIMATE 2 ON APPLE SILICON、32GB M5、PASS / NOT SOLVED、512×512 / 17F、抽象execution diagram |
| 12 | Metrics | v2 02:55:37、v3 02:23:41、post swap17.76 / 17.69 GiB、model31.758971 GiB。Observed single runs、approximate runtime、storage≠RAMを併記 |
| 13 | Timeline | VACE DRIVER READY → v2 TECHNICAL PASS / VISUAL PARTIAL → v3 TECHNICAL PASS / VISUAL WORSE D → v4 VALIDATED / UNRUN |
| 14 | Memory | Available / Compressed / Swapのbefore→afterをCSS棒図で比較。共通0–32 GiB表示尺度。post-run ≠ peak、非加算・disk-backed swapを明示 |
| 15 | Findings | 6 knowledge cards。技術完走、identity崩壊、v3悪化、UI/backend差、swap制約、v4未実行 |
| 16 | Reproduction | 4段階restore案、環境pins・6モデルmanifest・実験/ artifact manifest・4workflowを参照。private入力差し替えとexact replay不可を明示 |
| 17 | Limitations | 長尺/multi-seed/peak/per-stage/solver equivalence/native INT8/将来nightly/権利判断の未確定を表示 |
| 18 | v4 | UNRUN維持。pose_end 1.0→0.7はdenoising progression。output・runtime・memory・visual resultを創作せず停止理由を表示 |
| 19 | Responsive | 1440 / 1024 / 768 / 390 / 320pxで確認。6 disclosures展開時にもdocument scrollWidth=clientWidth。mobileのtimelineとlarge metricsは縦stack |
| 20 | Accessibility | semantic headings、skip link、native details、3px cyan keyboard focus、text status、意味のあるaria labels、decorative図のaria-hidden。主要文字色コントラスト最小8.22:1 |
| 21 | Performance | HTML+CSS 49,451 bytes。JS・外部font・CDN・private mediaなし。主要内容はJS offでも読める |
| 22 | Dependency | HTML / CSSのみ。framework、npm dependency、package manager導入なし |
| 23 | Privacy | site内absolute local path / private username / private media / model weightなし。公開予定アカウントとbrand URLは意図的 |
| 24 | Data consistency | manifestのruntime4表示・memory14表示・6モデルbytes合計34,100,935,705を照合。4実験 / 50artifact / 84pinsも確認 |
| 25 | Base path | assetsとknowledgeは相対URL。模擬project subpath配下の19 unique HTTP routesが200かつ保存bytes一致。root /assets不使用 |
| 26 | Showcase plan | docs/showcase-integration-plan.mdにtitle/category/kind/year/URL/repo/説明/後Phase16:9 poster案を記録。main Showcase未編集 |
| 27 | Source knowledge | 元local-aiを編集せず、元4workflow SHAを再照合。staging既存docs/model/artifact manifestも不変。site/knowledgeの21コピーはcanonicalとbyte-identical |
| 28 | Validation | 下記20必須site項目＋9 integrity/accessibility項目＝29静的チェックPASS。初期browser checksもPASS |
| 29 | Browser QA readiness | 次の詳細なbrowser visual QAへ進める。H2cでは初期表示・overflow・details・focusを確認。全screen-reader / 各browserの包括QAは別途 |
| 30 | Stop boundary | git init/add/commit/remote、GitHub repo作成/push/Pages enable、model削除/download、package install、新規generationなし。一時localhost previewを停止 |

## Site file tree

```text
site/
├── index.html
├── README.md
├── assets/
│   └── css/site.css
└── knowledge/
    ├── .gitignore
    ├── README.md
    ├── LICENSE-PLAN.md
    ├── THIRD_PARTY_NOTICES.md
    ├── docs/             既存8文書
    ├── manifests/        models.json / experiments.json / artifacts.json / environment.txt
    ├── results/README.md
    └── workflows/        VACE 1件 / Animate v2・v3・v4 3件
```

新規設計/検証文書: docs/pages-design-foundation.md、docs/showcase-integration-plan.md、本書。これらはsite/knowledgeにはコピーしていない。

## 必須site検証20項目

| # | 検証 | 結果 |
|---|---|---|
| 1 | index.html存在 | PASS |
| 2 | CSS存在 | PASS |
| 3 | JS不使用・主要内容は静的HTML | PASS |
| 4 | 相対リンクとMarkdown内リンク解決 | PASS |
| 5 | 絶対ローカルパスなし | PASS |
| 6 | private username / character identity漏洩なし | PASS |
| 7 | private media非同梱 | PASS |
| 8 | model weights非同梱 | PASS |
| 9 | 数値は凍結資料由来 | PASS |
| 10 | v4 UNRUN維持 | PASS |
| 11 | runtime一致 | PASS |
| 12 | memory値一致 | PASS |
| 13 | モデル総量一致 | PASS |
| 14 | 技術成功とvisual結果を分離 | PASS |
| 15 | responsive CSS・320px実表示確認 | PASS |
| 16 | prefers-reduced-motion | PASS |
| 17 | framework / CDN依存なし | PASS |
| 18 | package追加・installなし | PASS |
| 19 | Pages subpath安全 | PASS |
| 20 | HTML基本構造・ID・anchor正常 | PASS |

追加9項目: README clarification、JSON parse、v3 separation、v4 separation、existing result/SHA/status semantics、only two original files changed、21 evidence copies byte-identical、keyboard/status accessibility、no Git initialization。

## Browser確認の実測

| Viewport | Document clientWidth / scrollWidth | 結果 |
|---|---|---|
| 1440px | 1425 / 1425 | 横scrollなし |
| 1024px | 1009 / 1009 | 横scrollなし |
| 768px | 753 / 753 | 横scrollなし |
| 390px | 375 / 375 | 横scrollなし・縦stack |
| 320px | 305 / 305 | 横scrollなし・縦stack |

縦scrollbarを含むviewport幅とdocument clientWidthを分けて検証した。320pxのbody最小幅によるはみ出しを修正済み。6 detailsすべて開いた状態で再確認。Focus outlineはrgb(105,223,235) solid 3px。Console error / warning記録なし。

主要text paletteを使用する背景4色に対して照合: text16.82、muted9.39、green14.00、cyan11.11、amber10.54、red8.22、button15.01（比率）。これは主要文字色の静的照合であり、包括的なWCAG認証ではない。

## 将来の公開に向けた残事項

- 詳細browser visual QAと任意の専用16:9 poster。
- Repositoryのlicense決定と、site/の内容をPages artifact rootへ置くdeployment方式の決定。
- 別PhaseでGitHub公開/Pages enable後、実URLを検証してmain Works entryを追加。
- Canonical knowledge変更時にはsite/knowledgeコピーを更新し、SHA一致とvisible metricsを再照合。

ここでH2cを停止。公開・追加実験・model削除は行わない。
