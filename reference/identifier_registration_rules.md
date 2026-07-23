# ID登録 記述ルール（公式準拠）

ID登録では、識別子の値と、その識別子を登録した機関を一組で記載します。
識別子のURLではなく、識別子文字列そのものを記載する点に注意が必要です。

このファイルは、JPCOARスキーマ **2.0** の公式説明ページから、ID登録要素の定義、属性、記述ルールを整理したものです。
記載内容は、次の公式ページのみを典拠とします。

- [#19 ID登録（`jpcoar:identifierRegistration`）](https://schema.irdb.nii.ac.jp/ja/schema/2.0/19)

> このファイルには、公式説明ページに記載されたスキーマ層の情報だけを収録します。
> DOI登録要件と本ガイド独自の運用方針は含みません。
> 記入レベル記号は [フローチャート共通規約](../decision-trees/CONVENTIONS.md)、実務上の判断手順は [ID登録入力フローチャート](../decision-trees/identifier-registration.md)、DOI登録要件は [JPCOAR、JaLC、Crossref要件対照表](JPCOAR_JaLC_Crossref_requirements.md) を参照してください。

---

## #19 ID登録 `jpcoar:identifierRegistration`

### 定義

| 項目 | 内容 |
|------|------|
| 要素名 | `jpcoar:identifierRegistration` |
| 記入レベル | **MA（該当する場合は必須）** |
| 繰返回数 | **0-1（繰返不可、必須以外）** |
| 親要素 | なし |
| 要素の内容 | **DOI などの識別子の値そのもの**（識別子文字列） |

### 属性

| 属性 | 記入レベル | 繰返回数 | 値と備考 |
|------|-----------|----------|----------|
| `identifierType` | **M（必須）** | 1（繰返不可） | 統制語彙から1つ選択（下表） |

#### `identifierType` 統制語彙

| 値 | 意味 |
|----|------|
| `JaLC` | ジャパンリンクセンター DOI |
| `Crossref` | Crossref DOI |
| `DataCite` | DataCite DOI |
| `PMID` | 【現在不使用】PubMed ID |

### 記述ルール

- ID登録は、JaLC、Crossref、DataCite などへ識別子（DOI等）を登録する場合に記入する。
- 資源自身の識別子は、識別子（#18）に記入する。
- ID登録は、JaLCとのデータ連携のためにのみ使用する。
- 要素の内容には、登録した識別子の値をそのまま記入する。
  例えば、DOIのサフィックスを含む文字列が該当する。
- `identifierType` 属性で、その値がどの登録機関の識別子かを示す。
- JaLC DOI と Crossref DOI は、junii2 の `selfDOI` に対応する。
- JaLCでDOIを登録する場合は、`identifierRegistration` だけでなく `identifier`（#18）要素にも、`identifierType="DOI"` を指定し、HTTP URI形式（`https://doi.org/...`）で記入する必要がある。
- DOI登録の詳細は、[IRDBデータ提供機関のためのDOI管理・メタデータ入力ガイドライン：JPCOARスキーマ編](http://id.nii.ac.jp/1458/00000135/)に従う。

### 非推奨

- URIスキーム `info:doi/` や `doi:` を要素内容に使用することは禁止。
- DOIのURL表記（`https://doi.org/...` 等）を `identifierRegistration` の要素内容に使用することは禁止。
  `identifierRegistration` には、サフィックスを含む識別子文字列そのものを記入する。
  URL表記は `identifier`（#18）側で扱う。

### 入力例

```xml
<jpcoar:identifierRegistration identifierType="JaLC">10.18926/AMO/54590</jpcoar:identifierRegistration>
```

---

## マッピング（参考）

| 要素 | 対応 |
|------|------|
| `jpcoar:identifierRegistration` | `selfDOI`（JaLC DOI） |
| `identifierType` | `ra`（RA属性） |

> 出典：上記のJPCOARスキーマ 2.0 公式説明ページ（#19）
