# 今後の計画（ROADMAP）

JPCOARスキーマ 2.0 の決定木整備の着手順をまとめます。優先順位は **DOI登録（JaLC / Crossref）の必須項目** を最上位とし、必須度・`xml:lang` 要件は [JPCOAR/JaLC対照表 ver.1.5](reference/JPCOAR_JaLC_Crossref_requirements.md) に準拠します。進捗は各 [Issue](https://github.com/tzhaya/jpcoarschema-helper/issues) で管理します。

## 現在の状況

| プロパティ | 状態 |
|-----------|------|
| タイトル（#1, #2） | ✅ 作成済（雛形 → 確定作業は [#6](https://github.com/tzhaya/jpcoarschema-helper/issues/6)） |
| 作成者（#3） | ✅ 作成済 |

## フェーズ1: DOI登録の必須項目（最優先）

タイトル・作成者と合わせ、DOI登録に必須の中核項目をそろえます。**先に [#5 ID登録](https://github.com/tzhaya/jpcoarschema-helper/issues/5) を確定**させると、各決定木の冒頭分岐である「DOI登録先（JaLC / Crossref）」が定まり、以降の `xml:lang` 必須度が一貫します。

| 順 | プロパティ | 要素 | Issue | ねらい |
|----|-----------|------|-------|--------|
| 1 | ID登録 | `jpcoar:identifierRegistration`（#19） | [#5](https://github.com/tzhaya/jpcoarschema-helper/issues/5) | DOI登録先を確定するハブ。他決定木の前提となる |
| 2 | 識別子 | `jpcoar:identifier`（#18） | [#4](https://github.com/tzhaya/jpcoarschema-helper/issues/4) | 資源の所在（HDL > URI）。ID登録との違いを明確化 |
| 3 | 資源タイプ | `dc:type`（#15） | [#3](https://github.com/tzhaya/jpcoarschema-helper/issues/3) | ジャーナル系／書籍系を分岐させ後続の必須度を決める |
| 4 | 日付 | `datacite:date`（#12, #13） | [#1](https://github.com/tzhaya/jpcoarschema-helper/issues/1) | `dateType` 優先順位（Issued > dateGranted > Created > Updated） |
| 5 | 出版者 | `dc:publisher`（#10, #11） | [#2](https://github.com/tzhaya/jpcoarschema-helper/issues/2) | Crossref は `xml:lang="en"` 必須 |

> 番号は依存関係を踏まえた推奨順です。README の元の並び（日付→出版者→資源タイプ→識別子→ID登録）でも構いませんが、ID登録・資源タイプを先に固めると後工程の迷いが減ります。

## フェーズ2: 品質・運用基盤の整備

決定木が増える前に、テンプレートと自動チェックを整えます。

| プロパティ／作業 | Issue |
|-----------------|-------|
| `title.md`（雛形）を確定版に引き上げ | [#6](https://github.com/tzhaya/jpcoarschema-helper/issues/6) |
| 決定木一覧の二重メンテ解消（README 進捗の一元化） | [#7](https://github.com/tzhaya/jpcoarschema-helper/issues/7) |
| Issue テンプレート / CONTRIBUTING の整備 | [#9](https://github.com/tzhaya/jpcoarschema-helper/issues/9) |
| CI: Mermaid 構文チェック・リンクチェック | [#10](https://github.com/tzhaya/jpcoarschema-helper/issues/10) |

## フェーズ3: 残りプロパティの拡充

DOI必須以外のプロパティを、対照表の必須度を目安に順次決定木化します。着手時に [トラッキング Issue #8](https://github.com/tzhaya/jpcoarschema-helper/issues/8) から個別 Issue を切り出します。

- **優先度・高**: 収録物名／収録物識別子／巻・号／開始・終了ページ／関連情報（Crossref で必須になる項目）
- **優先度・中**: 寄与者・アクセス権・権利情報・主題・内容記述・言語・バージョン・助成情報・ファイル情報
- **優先度・低**: 時間的範囲・位置情報・学位系・会議記述・版・部編名 ほか（資源種別依存）

## 進め方の原則

- 1プロパティ＝1ページ（`decision-trees/*.md`）、共通テンプレート（記号凡例 → 決定木(Mermaid) → 決定プロセス対応表 → 注記 → 参考）に準拠。
- 必須度・`xml:lang` 要件は必ず [対照表](reference/JPCOAR_JaLC_Crossref_requirements.md) を典拠とする。
- ページ追加時は [decision-trees/README.md](decision-trees/README.md) とルート [README.md](README.md) の一覧を更新する（[#7](https://github.com/tzhaya/jpcoarschema-helper/issues/7) で運用を一元化予定）。
