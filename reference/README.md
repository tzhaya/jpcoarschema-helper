# 参照資料

入力フローチャートの判断は、公式のスキーマ定義だけでは決まりません。
要素と属性はJPCOARスキーマ、DOI登録時の必須度はJaLCおよびCrossrefの要件を確認する必要があります。

このディレクトリには、[decision-trees](../decision-trees/) のフローチャートが典拠とする資料を収録しています。
各フローチャートの要素名、記入レベル、`xml:lang`、DOI登録要件は、対応する資料に基づいています。

## 資料の使い分け

参照先は、確認したい内容によって異なります。

| 確認したい内容 | 参照する資料 |
|----------------|--------------|
| 要素番号と公式説明ページ | [JPCOARschema_guide.md](JPCOARschema_guide.md) |
| 要素、属性、記入レベル、繰返回数、統制語彙 | 各要素の `*_rules.md` |
| JaLC DOIとCrossref DOIの必須度 | [JPCOAR_JaLC_Crossref_requirements.md](JPCOAR_JaLC_Crossref_requirements.md) |
| 入力時の判断手順と本ガイドの運用方針 | [decision-trees](../decision-trees/) |

`*_rules.md` には、公式説明ページの情報だけを記載します。
DOI登録要件や本ガイドの運用方針は混ぜません。

## 収録資料

| ファイル | 内容 | 出典 |
|----------|------|------|
| [JPCOAR_JaLC_Crossref_requirements.md](JPCOAR_JaLC_Crossref_requirements.md) | ジャーナルアーティクルと書籍の必須項目、JaLC DOIとCrossref DOIの要件差 | JPCOAR/JaLC対照表 付録 ver.1.5（2025年11月） |
| [JPCOARschema_guide.md](JPCOARschema_guide.md) | JPCOARスキーマ 1.0.2と2.0の項番、公式説明ページへのリンク | [JPCOARスキーマ](https://schema.irdb.nii.ac.jp/ja/schema) |
| [title_rules.md](title_rules.md) | タイトル（#1）とその他のタイトル（#2）の記入レベル、属性、記述ルール | [JPCOARスキーマ 2.0 #1](https://schema.irdb.nii.ac.jp/ja/schema/2.0/1)、[#2](https://schema.irdb.nii.ac.jp/ja/schema/2.0/2) |
| [creator_rules.md](creator_rules.md) | 作成者（#3）と、識別子、姓名、姓、名、別名、所属の各下位項目 | [JPCOARスキーマ 2.0 #3](https://schema.irdb.nii.ac.jp/ja/schema/2.0/3) ほか各下位項目 |
| [date_rules.md](date_rules.md) | 日付（#12）と日付（リテラル）（#13）の記入レベル、属性、`dateType` 統制語彙 | [JPCOARスキーマ 2.0 #12](https://schema.irdb.nii.ac.jp/ja/schema/2.0/12)、[#13](https://schema.irdb.nii.ac.jp/ja/schema/2.0/13) |
| [resource_type_rules.md](resource_type_rules.md) | 資源タイプ（#15）の記入レベル、`rdf:resource` 属性、COAR統制語彙 | [JPCOARスキーマ 2.0 #15](https://schema.irdb.nii.ac.jp/ja/schema/2.0/15)、[資源タイプ語彙別表【Ver2.0】](https://schema.irdb.nii.ac.jp/ja/2.0/resource_type_vocabulary) |
| [identifier_rules.md](identifier_rules.md) | 識別子（#18）の記入レベル、属性、`identifierType` 統制語彙 | [JPCOARスキーマ 2.0 #18](https://schema.irdb.nii.ac.jp/ja/schema/2.0/18) |
| [identifier_registration_rules.md](identifier_registration_rules.md) | ID登録（#19）の記入レベル、属性、`identifierType` 統制語彙 | [JPCOARスキーマ 2.0 #19](https://schema.irdb.nii.ac.jp/ja/schema/2.0/19) |
| [_TEMPLATE_element_rules.md](_TEMPLATE_element_rules.md) | 新しい要素別ルール `*_rules.md` を作成するためのテンプレート | テンプレート |

新しいプロパティを追加するときは、[_TEMPLATE_element_rules.md](_TEMPLATE_element_rules.md) をコピーします。
公式説明ページから主要素と下位項目を一つずつ確認し、記入レベル、繰返回数、属性、統制語彙、記述ルール、入力例を転記します。
記入レベル記号は [フローチャート共通規約](../decision-trees/CONVENTIONS.md) を参照してください。
作成と照合の手順は、`jpcoar-flowchart` スキルに定義しています。

## 関連リンク

- [JPCOARスキーマ（公式）](https://schema.irdb.nii.ac.jp/ja/schema)
- [Subirats, I. and Zeng, M.L. 2020. *Linked Open Data Enabled Bibliographical Data (LODE-BD) 3.0*. Rome, FAO.](https://doi.org/10.4060/cb2209en)

> FAOのLODE-BD 3.0本体（PDF）は、第三者著作物（CC BY-NC-SA 3.0 IGO）のためリポジトリには収録していません。
> 上記のDOIから参照してください。
