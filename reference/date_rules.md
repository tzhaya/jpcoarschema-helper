# 日付 記述ルール（公式準拠）

JPCOARスキーマ **2.0** の公式説明ページに記載された、日付関連要素の記述ルールをまとめたものです。本書の記述はすべて以下の公式ページを典拠とします。

- #12 日付（`datacite:date`）: https://schema.irdb.nii.ac.jp/ja/schema/2.0/12
- #13 日付（リテラル）（`dcterms:date`）: https://schema.irdb.nii.ac.jp/ja/schema/2.0/13

> このファイルは公式記述の要約であり、運用上の補足や DOI 登録要件は含みません。記入レベル記号の意味は [decision-trees/CONVENTIONS.md](../decision-trees/CONVENTIONS.md)、実務向けの判断手順は [decision-trees/date.md](../decision-trees/date.md)、DOI 要件は [JPCOAR_JaLC_Crossref_requirements.md](JPCOAR_JaLC_Crossref_requirements.md) を参照してください。

---

## 記入レベル・繰返回数の凡例

| 記号 | 意味 |
|------|------|
| M | 必須（Mandatory） |
| MA | 該当する場合は必須（Mandatory if Applicable） |
| O | 任意（Optional） |
| 1 | 1回のみ（繰返不可） |
| 0-N | 0回以上、繰返可（必須以外） |
| 0-1 | 0〜1回、繰返不可 |

---

## #12 日付 `datacite:date`

### 定義

| 項目 | 内容 |
|------|------|
| 要素名 | `datacite:date` |
| 記入レベル | **MA（該当する場合は必須）** |
| 繰返回数 | **0-N（繰返可：必須以外）** |
| 親要素 | なし |

### 属性

| 属性 | 記入レベル | 繰返回数 | 値・備考 |
|------|-----------|----------|----------|
| `dateType` | **M（必須）** | 1（繰返不可） | 統制語彙から1つ選択（下表） |

#### `dateType` 統制語彙

| 値 | 意味 |
|----|------|
| `Accepted` | 受理日 |
| `Available` | 利用開始日 |
| `Collected` | 収集日 |
| `Copyrighted` | 著作権発効日 |
| `Created` | 作成日 |
| `Issued` | 発行日 |
| `Submitted` | 提出日 |
| `Updated` | 最終更新日 |
| `Valid` | 有効期日 |

### 記述ルール

- 日付は W3C Date and Time Formats で規定する形式（`YYYY` / `YYYY-MM` / `YYYY-MM-DD` / `YYYY-MM-DDThh:mmTZD` など）で記入する。
- 日付の範囲は RKMS-ISO8601 に従い、`開始/終了` の形式で記入する（例: `2004-03-02/2005-06-02`）。
- 日付の種類は `dateType` 属性で示す。

### 入力例

```xml
<!-- 発行日 -->
<datacite:date dateType="Issued">2015-10-01</datacite:date>

<!-- 利用開始日 -->
<datacite:date dateType="Available">2016-01-01</datacite:date>

<!-- 日付範囲（収集日） -->
<datacite:date dateType="Collected">2004-03-02/2005-06-02</datacite:date>
```

---

## #13 日付（リテラル） `dcterms:date`

### 定義

| 項目 | 内容 |
|------|------|
| 要素名 | `dcterms:date` |
| 記入レベル | O（任意） |
| 繰返回数 | 0-N（繰返可） |
| 親要素 | なし |

### 属性

| 属性 | 記入レベル | 繰返回数 | 値・備考 |
|------|-----------|----------|----------|
| `xml:lang` | MA（該当する場合は必須） | 0-1 | 言語コード |

### 記述ルール

- 統制された形式（`datacite:date`）で記入できない日付情報を、リテラル（自由記述）で補完する。
- 西暦以外の表記（年号・干支など）や不確定な日付に用いる。
- 西暦紀年が分かる場合は、対応する `datacite:date` を併用することが推奨される。

### 入力例

```xml
<!-- 年号 -->
<dcterms:date xml:lang="zh-tw">崇禎17</dcterms:date>

<!-- 干支 -->
<dcterms:date xml:lang="ja">寛政壬子</dcterms:date>

<!-- 不明年 -->
<dcterms:date>19--</dcterms:date>
```

---

## `datacite:date` と `dcterms:date` の比較

| 観点 | `datacite:date`（#12） | `dcterms:date`（#13） |
|------|------------------------|------------------------|
| 記入レベル | MA | O（任意） |
| 繰返回数 | 0-N | 0-N |
| 値の形式 | W3C DTF の統制形式 | リテラル（自由記述） |
| 種類の指定 | `dateType`（必須） | なし |
| 言語属性 | なし | `xml:lang`（MA） |
| 主な用途 | 西暦の確定した日付 | 年号・干支・不確定年などの補完 |

---

## マッピング（参考）

| 要素 | 対応 |
|------|------|
| `datacite:date` / `dateType` | DataCite `date` / `dateType` |

> 出典: 上記 JPCOARスキーマ 2.0 公式説明ページ（#12 / #13）
</content>
