# JPCOARスキーマ 入力フローチャート集

FAO の Linked Open Data Enabled Bibliographical Data (LODE-BD) 3.0 を参考に、JPCOARスキーマ（2.0）の各プロパティを初心者が迷わず入力できるようにするガイド集です。各ページは **フローチャート（Mermaid）＋ 入力プロセス対応表 ＋ 注記** で構成します。

DOI登録（JaLC / Crossref）を重視し、必須度・`xml:lang` 要件は [JPCOAR/JaLC対照表 ver.1.5](../reference/JPCOAR_JaLC_Crossref_requirements.md) に準拠します。

## 一覧

| プロパティ | 状態 | ページ |
|-----------|------|--------|
| タイトル | ✅ 作成済（雛形） | [title.md](title.md) |
| 作成者 | ✅ 作成済 | [creator.md](creator.md) |
| 日付 | 予定 | ― |
| 出版者 | 予定 | ― |
| 資源タイプ | 予定 | ― |
| 識別子 | 予定 | ― |
| ID登録 | 予定 | ― |

> 展開順は DOI登録の必須項目（作成者→日付→出版者→資源タイプ→識別子→ID登録）を優先します。

## 共通テンプレート

`title.md` の構成（記号凡例 → フローチャート → 対応表 → 注記 → 参考）を各プロパティの雛形として再利用します。
