# 識別子 記述ルール（公式準拠）

識別子では、値だけでなく、その値が属する識別子体系も指定します。
同じ文字列でも、`identifierType` が異なれば意味は変わります。

このファイルは、JPCOARスキーマ **2.0** の公式説明ページから、識別子の定義、属性、記述ルールを整理したものです。
記載内容は、次の公式ページのみを典拠とします。

- [#18 識別子（`jpcoar:identifier`）](https://schema.irdb.nii.ac.jp/ja/schema/2.0/18)

> このファイルには、公式説明ページに記載されたスキーマ層の情報だけを収録します。
> DOI登録要件と本ガイド独自の運用方針は含みません。
> 記入レベル記号は [フローチャート共通規約](../decision-trees/CONVENTIONS.md)、実務上の判断手順は [識別子入力フローチャート](../decision-trees/identifier.md)、DOI登録要件は [JPCOAR、JaLC、Crossref要件対照表](JPCOAR_JaLC_Crossref_requirements.md) を参照してください。

---

## #18 識別子 `jpcoar:identifier`

### 定義

| 項目 | 内容 |
|------|------|
| 要素名 | `jpcoar:identifier` |
| 記入レベル | **M（必須）** |
| 繰返回数 | **1-N（繰返可能・必須）** |
| 親要素 | なし |
| 要素の内容 | ユニークなID（識別子文字列） |

### 属性

| 属性 | 記入レベル | 繰返回数 | 値・備考 |
|------|-----------|----------|----------|
| `identifierType` | **M（必須）** | 1（繰返不可） | 統制語彙から1つ選択（下表） |

#### `identifierType` 統制語彙

| 値 | 意味 |
|----|------|
| `DOI` | デジタルオブジェクト識別子（DOI: Digital Object Identifier） |
| `HDL` | ハンドルシステム識別子（Handle URL） |
| `URI` | 統一資源識別子（URI: Uniform Resource Identifier） |

### 記述ルール

- コンテンツを識別するユニークなIDを記入する。
- 記述方法は、選択したスキーマ（識別子体系）に従う。
- リポジトリコンテンツ自身のIDを記入する。
- 学術雑誌論文の出版社版等のDOIは、`jpcoar:identifier` ではなく `jpcoar:relation`（関連情報）に記入する。
- JaLC DOIを登録する場合は、本要素に加えて `jpcoar:identifierRegistration`（ID登録）にも登録するDOIを記入する。
- `jpcoar:identifierRegistration` では、DOIを `prefix/suffix` 形式で記入する。
- 記入時は必ず `identifierType` を指定する。

### 入力例

```xml
<jpcoar:identifier identifierType="HDL">http://hdl.handle.net/2115/64495</jpcoar:identifier>
```

公式説明ページには、`identifierType="DOI"` の入力値として `https://doi.org/10.18926/AMO/54590` も例示されています。

---

## マッピング（参考）

| 要素 | junii2 |
|------|--------|
| `jpcoar:identifier` | URI（資源識別子URI）、selfDOI（JaLC DOI） |

> 出典：上記のJPCOARスキーマ 2.0 公式説明ページ（#18）
> 公式説明ページはjunii2の2項目を列挙しており、`identifierType` との対応は記載していません。
> DC-NDL、DataCite等へのマッピングは、公式説明ページに記載されていません。
