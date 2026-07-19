# 今後の計画（ROADMAP）

フローチャートは、スキーマの項番どおりに増やせばよいわけではありません。
DOI登録に欠かせない項目が抜けていれば登録作業が止まり、判断負荷の高い項目が後回しになれば、入力者は境界事例で迷い続けます。

整備順は、**DOI登録（JaLC / Crossref）の必須度**と、入力時に必要な**人間の判断量**から決めます。
必須度と `xml:lang` 要件は [JPCOAR/JaLC対照表 ver.1.5](reference/JPCOAR_JaLC_Crossref_requirements.md) に準拠し、個別作業の進捗は [Issue](https://github.com/tzhaya/jpcoarschema-helper/issues) で管理します。
整備済みプロパティの一覧は、正本である [decision-trees/README.md の一覧表](decision-trees/README.md#一覧)を参照してください。本ファイルでは進捗を重複管理しません。

## フェーズ1 DOI登録を支える中核項目

DOI登録先を決める ID登録と、後続項目の必須度を左右する資源タイプを先に固めたことで、各フローチャートの分岐を同じ前提で記述できるようになりました。
タイトル、作成者、日付、識別子も整備済みです。

このフェーズで残るのは、出版者 `dc:publisher`（#10、#11 → [Issue #2](https://github.com/tzhaya/jpcoarschema-helper/issues/2)）です。
Crossref では英語名（`xml:lang="en"`）が必須になるため、単なる転記項目として扱うことはできません。

## フェーズ2 品質と運用基盤の整備

ページが増えるほど、一覧の更新漏れ、リンク切れ、Mermaid 構文エラーを目視だけで防ぐのは難しくなります。
雛形の確定、エッジケース検証、一覧の一元化、CI による Mermaid 構文チェックとリンクチェックは完了しました。

このフェーズで残るのは、Issue テンプレートと CONTRIBUTING の整備（[#9](https://github.com/tzhaya/jpcoarschema-helper/issues/9)）です。

## フェーズ3 残りプロパティの拡充

DOI必須項目の次に着手するべきなのは、項番の若い項目とは限りません。
資料を見ても答えが一意に決まらず、選択が別項目へ波及するものを先に整備します。

2026-07-04 の見直しでは、**入力時の人間の判断負荷**を優先度の基準に追加しました。
出版タイプと関連情報は版の判断が `relationType` に連動し、アクセス権はエンバーゴによって正しい値が時間とともに変わります。
どちらも書誌から写すだけでは決まらないため、優先度を高へ移しました。

着手時は [トラッキング Issue #8](https://github.com/tzhaya/jpcoarschema-helper/issues/8) から個別 Issue を切り出します。

- **優先度：高**　収録物名、収録物識別子、巻と号、開始ページと終了ページ（Crossref で必須になる項目）、出版タイプと関連情報（連動ページ → [#15](https://github.com/tzhaya/jpcoarschema-helper/issues/15)）、アクセス権（→ [#16](https://github.com/tzhaya/jpcoarschema-helper/issues/16)）、助成情報（→ [#14](https://github.com/tzhaya/jpcoarschema-helper/issues/14)）
- **優先度：中**　寄与者（完了した [#12](https://github.com/tzhaya/jpcoarschema-helper/issues/12) タスク1a の creator/contributor 境界検証を流用）、権利情報、主題、内容記述、言語、バージョン情報、ファイル情報
- **優先度：低**　時間的範囲、位置情報、学位系、会議記述、版、部編名など（資源種別に依存）

## 進め方の原則

- 1プロパティにつき、入力ガイド `decision-trees/*.md` と公式定義のまとめ `reference/*_rules.md` を対で作成する。
- 入力ガイドは、項目の性質、早見表、Mermaid フローチャート、対応表、使い分け、入力例、注記、参考の共通構成に揃える。
- スキーマの公式定義、DOI登録要件、本ガイドの運用方針を混同しない。
- DOI登録の必須度と `xml:lang` 要件は、必ず [対照表](reference/JPCOAR_JaLC_Crossref_requirements.md) を典拠とする。
- ページ追加時は、フローチャート一覧・進捗の正本である [decision-trees/README.md](decision-trees/README.md) を更新する。ルール追加時は [reference/README.md](reference/README.md) も更新する。
