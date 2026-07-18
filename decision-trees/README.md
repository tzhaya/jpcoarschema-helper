# JPCOARスキーマ 入力フローチャート集

FAO の Linked Open Data Enabled Bibliographical Data (LODE-BD) 3.0 を参考に、JPCOARスキーマ（2.0）の各プロパティを初心者が迷わず入力できるようにするガイド集です。各ページは **フローチャート（Mermaid）＋ 入力プロセス対応表 ＋ 注記** で構成します。

DOI登録（JaLC / Crossref）を重視し、必須度・`xml:lang` 要件は [JPCOAR/JaLC対照表 ver.1.5](../reference/JPCOAR_JaLC_Crossref_requirements.md) に準拠します。

## 一覧

この表がフローチャート一覧と整備状況の正本です。
ページを追加したとき、または状態を変更したときは、この表だけを更新します。

| プロパティ | 状態 | ページ | 対象要素 |
|-----------|------|--------|----------|
| タイトル | ✅ 作成済み | [title.md](title.md) | `dc:title` / `dcterms:alternative`（#1、#2） |
| 作成者 | ✅ 作成済み | [creator.md](creator.md) | `jpcoar:creator` と下位項目（#3） |
| 日付 | ✅ 作成済み | [date.md](date.md) | `datacite:date` / `dcterms:date`（#12、#13） |
| 出版者 | 予定 | ― | `dc:publisher`（#10、#11） |
| 資源タイプ | ✅ 作成済み | [resource-type.md](resource-type.md) | `dc:type`（#15） |
| 識別子 | ✅ 作成済み | [identifier.md](identifier.md) | `jpcoar:identifier`（#18） |
| ID登録 | ✅ 作成済み | [identifier-registration.md](identifier-registration.md) | `jpcoar:identifierRegistration`（#19） |

> 展開順は DOI登録の必須項目（作成者→日付→出版者→資源タイプ→識別子→ID登録）を優先します。

## 共通テンプレート・規約

- 各ページ共通の記号凡例・記入レベル凡例・`xml:lang` 運用方針・3層の原則は [CONVENTIONS.md](CONVENTIONS.md) に集約しています。
- `title.md` の構成（まず入力するもの → フローチャート → 対応表 → 使い分け → 入力例 → 注記 → 参考）を各プロパティの雛形として再利用します。
- 要素定義のまとめは [reference/_TEMPLATE_element_rules.md](../reference/_TEMPLATE_element_rules.md) をコピーして作成します。
- 作成手順（公式定義のまとめ → DOI要件を加えてフローチャート化 → 照合）は `jpcoar-flowchart` スキルに定義しています。
