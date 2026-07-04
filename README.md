# jpcoarschema-helper

JPCOARスキーマ 2.0 の各項目を初心者が迷わず入力できるよう、FAO の [LODE-BD 3.0](https://doi.org/10.4060/cb2209en) を参考に作成したガイド集です。

フローチャートで入力の道筋をたどり、対応表で使用する要素・属性と実例を確定します。
GitHub 上で Mermaid 図がそのまま描画されます。

## 対象

- JPCOARスキーマ **2.0**
- 利用シーン: **DOI登録（JaLC / Crossref）を重視**した機関リポジトリ登録作業

## フローチャート一覧

| 項目 | ファイル | 対象要素 |
|------|----------|----------|
| タイトル | [decision-trees/title.md](decision-trees/title.md) | `dc:title` / `dcterms:alternative` (#1, #2) |
| 作成者 | [decision-trees/creator.md](decision-trees/creator.md) | `jpcoar:creator` と下位項目 (#3) |
| 日付 | [decision-trees/date.md](decision-trees/date.md) | `datacite:date` / `dcterms:date` (#12, #13) |

## 使い方

1. 登録したい項目のフローチャートファイルを開く
2. フローチャートの「資源／登録する文献」から出発し、分岐に従って進む
3. 対応表・注記で要素名・属性・入力例を確認する

## 入力項目の性質（評価の物差し）

JPCOARスキーマの入力項目は、作業の性質がそれぞれ異なります。本ガイドでは各項目を次の4観点で評価し、各フローチャートページの冒頭「**この項目の性質**」に明示しています。

| 観点 | 問い |
|------|------|
| 入力の型 | 資料の性質を**解釈**して統制語彙から選ぶのか（解釈型）、書誌から**写す**だけか（転記型）、外部を**調べて**決めるのか（調査型） |
| 他項目への影響 | その選択が他項目の必須度・値に波及するか |
| 事前調査 | 入力前に調べることがあるか（情報源はどこか） |
| 誤入力の影響 | 間違えた場合に何が起きるか（DOI登録エラー、公開ポリシー違反 など） |

**解釈型**で他項目への影響が大きい項目（資源タイプ・出版タイプ・アクセス権 など）ほど、フローチャートを丁寧にたどる価値があります。フローチャートの整備順もこの観点で優先度を付けています（→ [ROADMAP.md](ROADMAP.md)）。記載基準の詳細は [decision-trees/CONVENTIONS.md](decision-trees/CONVENTIONS.md) 第8節を参照してください。

## 今後の計画

フローチャート整備の着手順は [ROADMAP.md](ROADMAP.md) にまとめています。DOI登録の必須項目を最優先とし、進捗は [Issue](https://github.com/tzhaya/jpcoarschema-helper/issues) で管理します。

## 記号凡例（フローチャート共通）

| 記号 | 意味 |
|------|------|
| 楕円 `([ ])` | 開始 / 終了 |
| ひし形 `{ }` | 判断（Yes / No や種類の分岐） |
| 長方形 `[ ]` | 処理（入力・設定する内容） |
| 平行四辺形 `[/ /]` | 入力・情報源 |

## 参照資料

[reference/](reference/) に、各フローチャートが典拠とする資料を収録しています。

| ファイル | 内容 |
|----------|------|
| [JPCOAR_JaLC_Crossref_requirements.md](reference/JPCOAR_JaLC_Crossref_requirements.md) | ジャーナルアーティクル・書籍の必須項目と JaLC / Crossref DOI の差分マッピング |
| [JPCOARschema_guide.md](reference/JPCOARschema_guide.md) | JPCOARスキーマ各項目（1.0.2 / 2.0）の項番と公式説明ページへのリンク一覧 |

## 関連リンク

- [JPCOARスキーマ（公式）](https://schema.irdb.nii.ac.jp/ja/schema)
- [JAIRO Cloud](https://irdb.nii.ac.jp/)
- 手法の出典: Subirats, I. and Zeng, M.L. 2020. *Linked Open Data Enabled Bibliographical Data (LODE-BD) 3.0*. Rome, FAO. <https://doi.org/10.4060/cb2209en>

## ライセンス

このプロジェクトは [CC0 1.0 Universal (CC0 1.0) Public Domain Dedication](https://creativecommons.org/publicdomain/zero/1.0/) の下で公開されています。詳細は [LICENSE](LICENSE) ファイルを参照してください。

## 作者
- Takanori Hayashi