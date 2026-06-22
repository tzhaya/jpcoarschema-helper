# reference — 参照資料

[decision-trees](../decision-trees/) のフローチャートが典拠とする、JPCOARスキーマおよび DOI 登録要件の参照資料です。各フローチャートの必須度・`xml:lang` 要件・要素名はこれらの資料に準拠しています。

## 収録資料

| ファイル | 内容 | 出典 |
|----------|------|------|
| [JPCOAR_JaLC_Crossref_requirements.md](JPCOAR_JaLC_Crossref_requirements.md) | ジャーナルアーティクル・書籍の必須項目と JaLC DOI / Crossref DOI の差分マッピング | JPCOAR/JaLC対照表 付録 ver.1.5（2025年11月） |
| [JPCOARschema_guide.md](JPCOARschema_guide.md) | JPCOARスキーマ各項目（1.0.2 / 2.0）の項番と公式説明ページへのリンク一覧 | [JPCOARスキーマ](https://schema.irdb.nii.ac.jp/ja/schema) |
| [title_rules.md](title_rules.md) | タイトル（#1）／その他のタイトル（#2）の記入レベル・属性・記述ルールの公式準拠まとめ | [JPCOARスキーマ 2.0 #1](https://schema.irdb.nii.ac.jp/ja/schema/2.0/1) / [#2](https://schema.irdb.nii.ac.jp/ja/schema/2.0/2) |
| [_TEMPLATE_element_rules.md](_TEMPLATE_element_rules.md) | 要素別ルール（`*_rules.md`）作成用テンプレート。新規プロパティ追加時にコピーして使う | ― |

> 新しいプロパティのルールをまとめる際は `_TEMPLATE_element_rules.md` をコピーし、記入レベル記号の意味は [decision-trees/CONVENTIONS.md](../decision-trees/CONVENTIONS.md) を参照してください。作成手順は `jpcoar-flowchart` スキルに定義しています。

## 関連リンク

- JPCOARスキーマ（公式）: https://schema.irdb.nii.ac.jp/ja/schema
- 手法の出典 LODE-BD 3.0: Subirats, I. and Zeng, M.L. 2020. *Linked Open Data Enabled Bibliographical Data (LODE-BD) 3.0*. Rome, FAO. https://doi.org/10.4060/cb2209en

> FAO の LODE-BD 3.0 本体（PDF）は第三者著作物（CC BY-NC-SA 3.0 IGO）のためリポジトリには含めず、上記 DOI でリンク参照します。
