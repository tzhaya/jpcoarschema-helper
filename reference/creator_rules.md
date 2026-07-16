# 作成者 記述ルール（公式準拠）

作成者の記述は、氏名だけでは完結しません。
識別子、姓と名、別名、所属には、それぞれ異なる要素と属性が定められています。

このファイルは、JPCOARスキーマ **2.0** の公式説明ページから、作成者（`jpcoar:creator`）と下位項目の定義、属性、下位構造、記述ルールを整理したものです。
記載内容は、次の公式ページのみを典拠とします。

- [#3 作成者（`jpcoar:creator`）](https://schema.irdb.nii.ac.jp/ja/schema/2.0/3)
- [#3-.1 作成者識別子（`jpcoar:nameIdentifier`）](https://schema.irdb.nii.ac.jp/ja/schema/2.0/3-.1)
- [#3-.2 作成者姓名（`jpcoar:creatorName`）](https://schema.irdb.nii.ac.jp/ja/schema/2.0/3-.2)
- [#3-.3 作成者姓（`jpcoar:familyName`）](https://schema.irdb.nii.ac.jp/ja/schema/2.0/3-.3)
- [#3-.4 作成者名（`jpcoar:givenName`）](https://schema.irdb.nii.ac.jp/ja/schema/2.0/3-.4)
- [#3-.5 作成者別名（`jpcoar:creatorAlternative`）](https://schema.irdb.nii.ac.jp/ja/schema/2.0/3-.5)
- [#3-.6 作成者所属（`jpcoar:affiliation`）](https://schema.irdb.nii.ac.jp/ja/schema/2.0/3-.6)
- [#3-.6-.1 所属機関識別子（`jpcoar:nameIdentifier`）](https://schema.irdb.nii.ac.jp/ja/schema/2.0/3-.6-.1)
- [#3-.6-.2 所属機関名（`jpcoar:affiliationName`）](https://schema.irdb.nii.ac.jp/ja/schema/2.0/3-.6-.2)

> このファイルには、公式説明ページに記載されたスキーマ層の情報だけを収録します。
> DOI登録要件と本ガイド独自の運用方針は含みません。
> 記入レベル記号は [フローチャート共通規約](../decision-trees/CONVENTIONS.md)、実務上の判断手順は [作成者入力フローチャート](../decision-trees/creator.md)、DOI登録要件は [JPCOAR、JaLC、Crossref要件対照表](JPCOAR_JaLC_Crossref_requirements.md) を参照してください。

---

## #3 作成者 `jpcoar:creator`

### 定義

| 項目 | 内容 |
|------|------|
| 要素名 | `jpcoar:creator` |
| 記入レベル | **MA（該当する場合は必須）** |
| 繰返回数 | **0-N（繰返可：必須以外）** |
| 親要素 | なし |

### 属性

| 属性 | 記入レベル | 繰返回数 | 値・備考 |
|------|-----------|----------|----------|
| `creatorType` | O（任意） | 0-1 | コンテンツの作成に直接的に関わりを持つものの役割を簡潔に記入する（入力例では `creatorType="著"`） |

### 下位項目（入れ子構造）

| # | 要素名 | 記入レベル | 繰返回数 | 説明 |
|---|--------|-----------|----------|------|
| 3-.1 | `jpcoar:nameIdentifier` | MA | 0-N | 作成者識別子 |
| 3-.2 | `jpcoar:creatorName` | MA | 0-N | 作成者姓名 |
| 3-.3 | `jpcoar:familyName` | O | 0-N | 作成者姓 |
| 3-.4 | `jpcoar:givenName` | O | 0-N | 作成者名 |
| 3-.5 | `jpcoar:creatorAlternative` | O | 0-N | 作成者別名 |
| 3-.6 | `jpcoar:affiliation` | R | 0-N | 作成者所属（下位に所属機関識別子・所属機関名を持つ） |

### 記述ルール

- 学位論文の場合は必ず入力する。
- 複数の作成者がいる場合は、第一著者から順に記入する。
- コンテンツの作成に直接的に関与した者を「作成者」とする。
- 間接的に関与した者は「寄与者」（#4）として、作成者と明確に区別する。
- `contributorType` の統制語彙に該当する役割を持つ者は、作成者ではなく寄与者として記入する。

### 入力例

```xml
<jpcoar:creator creatorType="著">
    <jpcoar:nameIdentifier nameIdentifierScheme="ORCID"
        nameIdentifierURI="https://orcid.org/0000-0001-0002-0003">0000-0001-0002-0003</jpcoar:nameIdentifier>
    <jpcoar:creatorName xml:lang="ja">夏目, 漱石</jpcoar:creatorName>
    <jpcoar:creatorName xml:lang="en">Natsume, Soseki</jpcoar:creatorName>
    <jpcoar:creatorName xml:lang="ja-Kana">ナツメ, ソウセキ</jpcoar:creatorName>
    <jpcoar:familyName xml:lang="ja">夏目</jpcoar:familyName>
    <jpcoar:givenName xml:lang="ja">漱石</jpcoar:givenName>
    <jpcoar:creatorAlternative xml:lang="ja">夏目, 金之助</jpcoar:creatorAlternative>
    <jpcoar:creatorAlternative xml:lang="en">Natsume, Kinnosuke</jpcoar:creatorAlternative>
    <jpcoar:creatorAlternative xml:lang="ja-Kana">ナツメ, キンノスケ</jpcoar:creatorAlternative>
    <jpcoar:affiliation>
        <jpcoar:nameIdentifier nameIdentifierScheme="ISNI"
            nameIdentifierURI="http://www.isni.org/isni/0000000121691048">0000000121691048</jpcoar:nameIdentifier>
        <jpcoar:affiliationName xml:lang="en">The University of Tokyo</jpcoar:affiliationName>
    </jpcoar:affiliation>
</jpcoar:creator>
```

---

## #3-.1 作成者識別子 `jpcoar:nameIdentifier`

### 定義

| 項目 | 内容 |
|------|------|
| 要素名 | `jpcoar:nameIdentifier` |
| 記入レベル | MA（該当する場合は必須） |
| 繰返回数 | 0-N（繰返可） |
| 親要素 | `jpcoar:creator` |

### 属性

| 属性 | 記入レベル | 繰返回数 | 値・備考 |
|------|-----------|----------|----------|
| `nameIdentifierScheme` | M（必須） | 1 | 統制語彙: `e-Rad_Researcher` / `NRID`（非推奨） / `ORCID` / `ISNI` / `VIAF` / `AID` / `kakenhi`（非推奨） / `Ringgold` / `GRID`（非推奨） / `ROR` |
| `nameIdentifierURI` | MA | 0-1 | ID 確認ページへの HTTP URI（例: `https://orcid.org/0000-0001-0002-0003`） |

### 記述ルール

- 作成者を一意に識別する ID を記入する。
- `nameIdentifierScheme` でスキーマ名を指定する。
- 接頭辞等の情報を付けず、**ID のみを記入する**。
- URI は ID の確認ページへのリンク形式で `nameIdentifierURI` に記入する。

### 非推奨

- `nameIdentifier` の値に URL を含めること（ID のみを記入する）。
- スキーム `NRID` / `kakenhi` / `GRID` の使用。

### 入力例

```xml
<jpcoar:nameIdentifier nameIdentifierScheme="ORCID"
    nameIdentifierURI="https://orcid.org/0000-0001-0002-0003">0000-0001-0002-0003</jpcoar:nameIdentifier>
```

---

## #3-.2 作成者姓名 `jpcoar:creatorName`

### 定義

| 項目 | 内容 |
|------|------|
| 要素名 | `jpcoar:creatorName` |
| 記入レベル | MA（該当する場合は必須） |
| 繰返回数 | 0-N（繰返可） |
| 親要素 | `jpcoar:creator` |

### 属性

| 属性 | 記入レベル | 繰返回数 | 値・備考 |
|------|-----------|----------|----------|
| `xml:lang` | MA | 0-1 | 言語コード（`ja` / `en` / `ja-Kana` / `ja-Latn` 等） |
| `nameType` | R（推奨） | 0-1 | `Personal`（個人名、既定） / `Organizational`（団体名） |

### 記述ルール

- 作成者の姓名を記入する。
- 個人名は「姓△名」（姓・カンマ・スペース区切り）の形式で記入する。
- 各言語コードの `creatorName` の出現回数は 1 回までとする。
- 片仮名ヨミは `xml:lang="ja-Kana"`、ローマ字ヨミは `xml:lang="ja-Latn"` とする。

### 非推奨

- `xml:lang` の指定がない記入。

### 入力例

```xml
<jpcoar:creatorName xml:lang="ja">夏目, 漱石</jpcoar:creatorName>
<jpcoar:creatorName xml:lang="en">Natsume, Soseki</jpcoar:creatorName>
<jpcoar:creatorName xml:lang="ja-Kana">ナツメ, ソウセキ</jpcoar:creatorName>
```

---

## #3-.3 作成者姓 `jpcoar:familyName`

### 定義

| 項目 | 内容 |
|------|------|
| 要素名 | `jpcoar:familyName` |
| 記入レベル | O（任意） |
| 繰返回数 | 0-N（繰返可） |
| 親要素 | `jpcoar:creator` |

### 属性

| 属性 | 記入レベル | 繰返回数 | 値・備考 |
|------|-----------|----------|----------|
| `xml:lang` | MA | 0-1 | 言語コード |

### 記述ルール

- 作成者の姓を記入する。
- 作成者が個人であり、姓が判別可能な場合に記入する。
- 各言語コードの `familyName` の出現回数は 1 回までとする。

### 非推奨

- 日本語のヨミ（カナ・ローマ字）をこの要素に記入すること。
- 団体名を記入すること。

### 入力例

```xml
<jpcoar:familyName xml:lang="ja">夏目</jpcoar:familyName>
```

---

## #3-.4 作成者名 `jpcoar:givenName`

### 定義

| 項目 | 内容 |
|------|------|
| 要素名 | `jpcoar:givenName` |
| 記入レベル | O（任意） |
| 繰返回数 | 0-N（繰返可） |
| 親要素 | `jpcoar:creator` |

### 属性

| 属性 | 記入レベル | 繰返回数 | 値・備考 |
|------|-----------|----------|----------|
| `xml:lang` | MA | 0-1 | 言語コード |

### 記述ルール

- 作成者の名を記入する。
- 作成者が個人であり、名が判別可能な場合に記入する。
- ミドルネームがある場合は「ミドルネーム△名」の形式で記入する。
- 各言語コードの `givenName` の出現回数は 1 回までとする。

### 非推奨

- 日本語のヨミ（カナ・ローマ字）をこの要素に記入すること。
- 団体名を記入すること。

### 入力例

```xml
<jpcoar:givenName xml:lang="ja">漱石</jpcoar:givenName>
```

---

## #3-.5 作成者別名 `jpcoar:creatorAlternative`

### 定義

| 項目 | 内容 |
|------|------|
| 要素名 | `jpcoar:creatorAlternative` |
| 記入レベル | O（任意） |
| 繰返回数 | 0-N（繰返可） |
| 親要素 | `jpcoar:creator` |

### 属性

| 属性 | 記入レベル | 繰返回数 | 値・備考 |
|------|-----------|----------|----------|
| `xml:lang` | MA | 0-1 | 言語コード（片仮名ヨミ `ja-Kana` / ローマ字ヨミ `ja-Latn`） |

### 記述ルール

- 作成者の別名を記入する。
- 記述方法は作成者姓名（`jpcoar:creatorName`）に準じる。
- 片仮名ヨミは `xml:lang="ja-Kana"`、ローマ字ヨミは `xml:lang="ja-Latn"` とする。

### 入力例

```xml
<jpcoar:creatorAlternative xml:lang="ja">夏目, 金之助</jpcoar:creatorAlternative>
<jpcoar:creatorAlternative xml:lang="en">Natsume, Kinnosuke</jpcoar:creatorAlternative>
<jpcoar:creatorAlternative xml:lang="ja-Kana">ナツメ, キンノスケ</jpcoar:creatorAlternative>
```

---

## #3-.6 作成者所属 `jpcoar:affiliation`

### 定義

| 項目 | 内容 |
|------|------|
| 要素名 | `jpcoar:affiliation` |
| 記入レベル | R（推奨） |
| 繰返回数 | 0-N（繰返可） |
| 親要素 | `jpcoar:creator` |

### 属性

属性なし。

### 下位項目（入れ子構造）

| # | 要素名 | 記入レベル | 繰返回数 | 説明 |
|---|--------|-----------|----------|------|
| 3-.6-.1 | `jpcoar:nameIdentifier` | R | 0-N | 所属機関識別子 |
| 3-.6-.2 | `jpcoar:affiliationName` | R | 0-N | 所属機関名 |

### 記述ルール

- 作成者の所属する機関名を記入する。
- 下位の所属機関識別子（`jpcoar:nameIdentifier`）と所属機関名（`jpcoar:affiliationName`）で構成する。

### 入力例

```xml
<jpcoar:affiliation>
    <jpcoar:nameIdentifier nameIdentifierScheme="ISNI"
        nameIdentifierURI="http://www.isni.org/isni/0000000121691048">0000000121691048</jpcoar:nameIdentifier>
    <jpcoar:affiliationName xml:lang="en">The University of Tokyo</jpcoar:affiliationName>
</jpcoar:affiliation>
```

---

## #3-.6-.1 所属機関識別子 `jpcoar:nameIdentifier`

### 定義

| 項目 | 内容 |
|------|------|
| 要素名 | `jpcoar:nameIdentifier` |
| 記入レベル | R（推奨） |
| 繰返回数 | 0-N（繰返可） |
| 親要素 | `jpcoar:affiliation` |

### 属性

| 属性 | 記入レベル | 繰返回数 | 値・備考 |
|------|-----------|----------|----------|
| `nameIdentifierScheme` | M（必須） | 1 | 統制語彙: `kakenhi`（非推奨） / `ISNI` / `Ringgold` / `GRID`（非推奨） / `ROR` |
| `nameIdentifierURI` | R（推奨） | 0-1 | HTTP URI 形式。URI 未保有の場合は省略可 |

### 記述ルール

- 所属機関を一意に識別する ID を記入する。
- `nameIdentifierScheme` でスキーマ名を指定する。
- 接頭辞等の情報を付けず、**ID のみを記入する**。記述形式はスキーマに依存する（例: `000000012192178X`（ISNI）、`https://ror.org/057zh3y96`（ROR））。

### 非推奨

- スキーム `kakenhi` / `GRID` の使用。

### 入力例

```xml
<jpcoar:nameIdentifier nameIdentifierScheme="ISNI"
    nameIdentifierURI="http://www.isni.org/isni/0000000121691048">0000000121691048</jpcoar:nameIdentifier>
```

---

## #3-.6-.2 所属機関名 `jpcoar:affiliationName`

### 定義

| 項目 | 内容 |
|------|------|
| 要素名 | `jpcoar:affiliationName` |
| 記入レベル | R（推奨） |
| 繰返回数 | 0-N（繰返可） |
| 親要素 | `jpcoar:affiliation` |

### 属性

| 属性 | 記入レベル | 繰返回数 | 値・備考 |
|------|-----------|----------|----------|
| `xml:lang` | MA | 0-1 | 言語コード |

### 記述ルール

- 所属機関の名称を記入する。
- 略称ではなく正式名称を記入する。
- 機関名までとし、部局名などの下位階層は記入しない。
- コンテンツ作成時点の所属機関を記入する。
- 複数言語がある場合は、本文言語と同じ言語を最初に記入し、その後に別言語を続ける。
- 各言語コードの `affiliationName` の出現回数は 1 回までとする。

### 入力例

```xml
<jpcoar:affiliationName xml:lang="en">The University of Tokyo</jpcoar:affiliationName>
```

---

## 下位要素の比較

| 観点 | `creatorName`（3-.2） | `familyName`（3-.3） / `givenName`（3-.4） |
|------|----------------------|--------------------------------------------|
| 記入レベル | MA | O |
| 主な用途 | 姓名（または団体名）を 1 文字列で記入 | 個人名を姓・名に分けて記入 |
| 団体名 | 記入可（`nameType="Organizational"`） | 記入しない |
| 同一言語コードの重複 | 不可（各言語 1 回まで） | 不可（各言語 1 回まで） |
| ヨミ（`ja-Kana` / `ja-Latn`） | こちらに記入 | 記入しない |

---

## マッピング（参考）

| 要素 | junii2 |
|------|--------|
| `jpcoar:creator` / `jpcoar:creatorName` | creator |

> 出典：上記のJPCOARスキーマ 2.0 公式説明ページ（#3および下位項目）
