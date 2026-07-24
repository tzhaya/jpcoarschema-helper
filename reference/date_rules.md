# 日付 記述ルール（公式準拠）

日付には、統制形式で記載する要素と、自由記述で補完する要素があります。
同じ日付情報でも、値の形式によって入力先が異なります。

このファイルは、JPCOARスキーマ **2.0** の公式説明ページから、日付関連要素の定義、属性、記述ルールを整理したものです。
記載内容は、次の公式ページのみを典拠とします。

- [#12 日付（`datacite:date`）](https://schema.irdb.nii.ac.jp/ja/schema/2.0/12)
- [#13 日付（リテラル）（`dcterms:date`）](https://schema.irdb.nii.ac.jp/ja/schema/2.0/13)

> このファイルには、公式説明ページに記載されたスキーマ層の情報だけを収録します。
> DOI登録要件と本ガイド独自の運用方針は含みません。
> 記入レベル記号は [フローチャート共通規約](../decision-trees/CONVENTIONS.md)、実務上の判断手順は [日付入力フローチャート](../decision-trees/date.md)、DOI登録要件は [JPCOAR、JaLC、Crossref要件対照表](JPCOAR_JaLC_Crossref_requirements.md) を参照してください。

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

| 属性 | 記入レベル | 繰返回数 | 値と備考 |
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
- 日付の範囲は RKMS-ISO8601 に従い、`開始/終了` の形式で記入する。
  例として、`2004-03-02/2005-06-02` のように記載する。
- 日付の種類は `dateType` 属性で示す。
- `Issued`（発行日）がある場合は記入必須とする。
- その他の日付も、関連する情報がある場合は必ず記入する。
- `dcterms:accessRights`（アクセス権）が `embargoed access` の場合は、`dateType="Available"` で利用開始日を記入する。

### 非推奨

- `dateType` を省略してはならない。
- `datacite:date` に `19--` のような不明な年を記入してはならない。

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

| 属性 | 記入レベル | 繰返回数 | 値と備考 |
|------|-----------|----------|----------|
| `xml:lang` | MA（該当する場合は必須） | 0-1 | 言語コード |

### 記述ルール

- 統制された形式（`datacite:date`）で記入できない日付情報を、リテラル（自由記述）で補完する。
- 西暦以外の表記（年号、干支など）や不確定な日付に用いる。
- 西暦紀年は `datacite:date` に記入する。
- 不明な日付を除き、対応する `datacite:date` を併用することが推奨される。
- コンテンツの内容に関する時間的範囲は、時間的範囲（`dcterms:temporal`）に記入する。

### 非推奨

- `享和3 (1803)` のように、リテラルの日付へ西暦紀年を補記しない。
  西暦紀年は `datacite:date` に分けて記入する。

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
| 主な用途 | 西暦の確定した日付 | 年号、干支、不確定年などの補完 |
| 不明年 `19--` | 記入してはならない | 記入例あり |

---

## マッピング（参考）

| 要素 | junii2 |
|------|------|
| `datacite:date` | `date`（日付）、`dateofissued`（刊行年月日） |

> `dcterms:date`（#13）には、公式説明ページに junii2 マッピングの記載がありません。

> 出典：上記のJPCOARスキーマ 2.0 公式説明ページ（#12）
