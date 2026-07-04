# ID登録 記述ルール（公式準拠）

JPCOARスキーマ **2.0** の公式説明ページに記載された、ID登録関連要素の記述ルールをまとめたものです。本書の記述はすべて以下の公式ページを典拠とします。

- #19 ID登録（`jpcoar:identifierRegistration`）: https://schema.irdb.nii.ac.jp/ja/schema/2.0/19

> このファイルは公式記述の要約であり、運用上の補足や DOI 登録要件は含みません。記入レベル記号の意味は [decision-trees/CONVENTIONS.md](../decision-trees/CONVENTIONS.md)、実務向けの判断手順は [decision-trees/identifier-registration.md](../decision-trees/identifier-registration.md)、DOI 要件は [JPCOAR_JaLC_Crossref_requirements.md](JPCOAR_JaLC_Crossref_requirements.md) を参照してください。

---

## 記入レベル・繰返回数の凡例

| 記号 | 意味 |
|------|------|
| M | 必須（Mandatory） |
| MA | 該当する場合は必須（Mandatory if Applicable） |
| 1 | 1回のみ（繰返不可） |
| 0-1 | 0〜1回、繰返不可（必須以外） |

---

## #19 ID登録 `jpcoar:identifierRegistration`

### 定義

| 項目 | 内容 |
|------|------|
| 要素名 | `jpcoar:identifierRegistration` |
| 記入レベル | **MA（該当する場合は必須）** |
| 繰返回数 | **0-1（繰返不可・必須以外）** |
| 親要素 | なし |
| 要素の内容 | **DOI などの識別子の値そのもの**（識別子文字列） |

### 属性

| 属性 | 記入レベル | 繰返回数 | 値・備考 |
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

- ID登録は、JaLC・Crossref・DataCite などへ識別子（DOI等）を登録する場合に記入する。
- 要素の内容には、登録した識別子の値（例: DOIのサフィックスを含む文字列）をそのまま記入する。
- `identifierType` 属性で、その値がどの登録機関の識別子かを示す。
- JaLC で DOI を登録する場合は、`identifierRegistration` だけでなく `identifier`（#18）要素にも、HTTP URI 形式（`https://doi.org/...`）で記入する必要がある。

### 非推奨

- URI スキーム `info:doi/` や `doi:` を要素内容に使用することは禁止。
- DOI の URL 表記（`https://doi.org/...` 等）を `identifierRegistration` の要素内容に使用することは禁止（`identifierRegistration` にはサフィックスを含む識別子文字列そのものを記入し、URL 表記は `identifier`（#18）側で扱う）。

### 入力例

```xml
<jpcoar:identifierRegistration identifierType="JaLC">10.18926/AMO/54590</jpcoar:identifierRegistration>
```

---

## マッピング（参考）

| 要素 | 対応 |
|------|------|
| `jpcoar:identifierRegistration` / `identifierType` | 対応する上位語彙なし（JPCOAR固有） |

> 出典: 上記 JPCOARスキーマ 2.0 公式説明ページ（#19）
