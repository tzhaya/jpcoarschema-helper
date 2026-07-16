# 資源タイプ 記述ルール（公式準拠）

資源タイプでは、語彙名と、その語彙に対応するURIを組にして記述します。
語彙名が異なっても同じURIを共有する場合があるため、URIだけでは値を決められません。

このファイルは、JPCOARスキーマ **2.0** の公式説明ページから、資源タイプの定義、属性、統制語彙、記述ルールを整理したものです。
記載内容は、次の公式ページのみを典拠とします。

- [#15 資源タイプ（`dc:type`）](https://schema.irdb.nii.ac.jp/ja/schema/2.0/15)
- [資源タイプ語彙別表【Ver2.0】](https://schema.irdb.nii.ac.jp/ja/2.0/resource_type_vocabulary)

> このファイルには、公式説明ページに記載されたスキーマ層の情報だけを収録します。
> DOI登録要件と本ガイド独自の運用方針は含みません。
> 記入レベル記号は [フローチャート共通規約](../decision-trees/CONVENTIONS.md)、実務上の判断手順は [資源タイプ入力フローチャート](../decision-trees/resource-type.md)、DOI登録要件は [JPCOAR、JaLC、Crossref要件対照表](JPCOAR_JaLC_Crossref_requirements.md) を参照してください。

---

## #15 資源タイプ `dc:type`

### 定義

| 項目 | 内容 |
|------|------|
| 要素名 | `dc:type` |
| 記入レベル | M（必須） |
| 繰返回数 | 1（繰返不可：必須） |
| 統制語彙 | [資源タイプ語彙別表【Ver2.0】](https://schema.irdb.nii.ac.jp/ja/2.0/resource_type_vocabulary) |
| 親要素 | なし |

### 属性

| 属性 | 記入レベル | 繰返回数 | 値 |
|------|-----------|----------|-----|
| `rdf:resource` | M（必須） | 1（繰返不可：必須） | 選択した統制語彙に対応する COAR Resource Type の URI |

### 記述ルール

- コンテンツの種類を、資源タイプ語彙別表から選択して記入する。
- `rdf:resource` には、選択した統制語彙に対応する COAR Resource Type の URI を記入する。
- `departmental bulletin paper`（紀要論文）および `article`（記事）には、`journal article`（学術雑誌論文）と同じ URI `http://purl.org/coar/resource_type/c_6501` を記入する。

### 統制語彙

公式別表に掲載されている語彙を、カテゴリ別に示します。
公式別表のカテゴリ見出しは `Conference object` ですが、その配下の現行語彙名は `conference output` です。

| カテゴリ | 語彙 | `rdf:resource` |
|----------|------|----------------|
| Article | `conference paper` | `http://purl.org/coar/resource_type/c_5794` |
| Article | `data paper` | `http://purl.org/coar/resource_type/c_beb9` |
| Article | `departmental bulletin paper` | `http://purl.org/coar/resource_type/c_6501` |
| Article | `editorial` | `http://purl.org/coar/resource_type/c_b239` |
| Article | `journal` | `http://purl.org/coar/resource_type/c_0640/` |
| Article | `journal article` | `http://purl.org/coar/resource_type/c_6501` |
| Article | `newspaper` | `http://purl.org/coar/resource_type/c_2fe3` |
| Article | `review article` | `http://purl.org/coar/resource_type/c_dcae04bc` |
| Article | `other periodical` | `http://purl.org/coar/resource_type/QX5C-AR31/` |
| Article | `software paper` | `http://purl.org/coar/resource_type/c_7bab` |
| Article | `article` | `http://purl.org/coar/resource_type/c_6501` |
| Book | `book` | `http://purl.org/coar/resource_type/c_2f33` |
| Book | `book part` | `http://purl.org/coar/resource_type/c_3248` |
| Cartographic Material | `cartographic material` | `http://purl.org/coar/resource_type/c_12cc` |
| Cartographic Material | `map` | `http://purl.org/coar/resource_type/c_12cd` |
| Conference object | `conference output` | `http://purl.org/coar/resource_type/c_c94f` |
| Conference object | `conference presentation` | `http://purl.org/coar/resource_type/R60J-J5BD/` |
| Conference object | `conference proceedings` | `http://purl.org/coar/resource_type/c_f744` |
| Conference object | `conference poster` | `http://purl.org/coar/resource_type/c_6670` |
| Dataset | `aggregated data` | `http://purl.org/coar/resource_type/ACF7-8YT9/` |
| Dataset | `clinical trial data` | `http://purl.org/coar/resource_type/c_cb28/` |
| Dataset | `compiled data` | `http://purl.org/coar/resource_type/FXF3-D3G7/` |
| Dataset | `dataset` | `http://purl.org/coar/resource_type/c_ddb1` |
| Dataset | `encoded data` | `http://purl.org/coar/resource_type/AM6W-6QAW/` |
| Dataset | `experimental data` | `http://purl.org/coar/resource_type/63NG-B465/` |
| Dataset | `genomic data` | `http://purl.org/coar/resource_type/A8F1-NPV9/` |
| Dataset | `geospatial data` | `http://purl.org/coar/resource_type/2H0M-X761/` |
| Dataset | `laboratory notebook` | `http://purl.org/coar/resource_type/H41Y-FW7B/` |
| Dataset | `measurement and test data` | `http://purl.org/coar/resource_type/DD58-GFSX/` |
| Dataset | `observational data` | `http://purl.org/coar/resource_type/FF4C-28RK/` |
| Dataset | `recorded data` | `http://purl.org/coar/resource_type/CQMR-7K63/` |
| Dataset | `simulation data` | `http://purl.org/coar/resource_type/W2XT-7017/` |
| Dataset | `survey data` | `http://purl.org/coar/resource_type/NHD0-W6SY/` |
| Image | `image` | `http://purl.org/coar/resource_type/c_c513` |
| Image | `still image` | `http://purl.org/coar/resource_type/c_ecc8` |
| Image | `moving image` | `http://purl.org/coar/resource_type/c_8a7e` |
| Image | `video` | `http://purl.org/coar/resource_type/c_12ce` |
| Lecture | `lecture` | `http://purl.org/coar/resource_type/c_8544` |
| Patent | `design patent` | `http://purl.org/coar/resource_type/C53B-JCY5/` |
| Patent | `patent` | `http://purl.org/coar/resource_type/c_15cd` |
| Patent | `PCT application` | `http://purl.org/coar/resource_type/SB3Y-W4EH/` |
| Patent | `plant patent` | `http://purl.org/coar/resource_type/Z907-YMBB/` |
| Patent | `plant variety protection` | `http://purl.org/coar/resource_type/GPQ7-G5VE/` |
| Patent | `software patent` | `http://purl.org/coar/resource_type/MW8G-3CR8/` |
| Patent | `trademark` | `http://purl.org/coar/resource_type/H6QP-SC1X/` |
| Patent | `utility model` | `http://purl.org/coar/resource_type/9DKX-KSAF/` |
| Report | `report` | `http://purl.org/coar/resource_type/c_93fc` |
| Report | `research report` | `http://purl.org/coar/resource_type/c_18ws` |
| Report | `technical report` | `http://purl.org/coar/resource_type/c_18gh` |
| Report | `policy report` | `http://purl.org/coar/resource_type/c_186u` |
| Report | `working paper` | `http://purl.org/coar/resource_type/c_8042` |
| Report | `data management plan` | `http://purl.org/coar/resource_type/c_ab20` |
| Sound | `sound` | `http://purl.org/coar/resource_type/c_18cc` |
| Thesis | `thesis` | `http://purl.org/coar/resource_type/c_46ec` |
| Thesis | `bachelor thesis` | `http://purl.org/coar/resource_type/c_7a1f` |
| Thesis | `master thesis` | `http://purl.org/coar/resource_type/c_bdcc` |
| Thesis | `doctoral thesis` | `http://purl.org/coar/resource_type/c_db06` |
| Multiple | `commentary` | `http://purl.org/coar/resource_type/D97F-VB57/` |
| Multiple | `design` | `http://purl.org/coar/resource_type/542X-3S04/` |
| Multiple | `industrial design` | `http://purl.org/coar/resource_type/JBNF-DYAD/` |
| Multiple | `interactive resource` | `http://purl.org/coar/resource_type/c_e9a0` |
| Multiple | `layout design` | `http://purl.org/coar/resource_type/BW7T-YM2G/` |
| Multiple | `learning object` | `http://purl.org/coar/resource_type/c_e059` |
| Multiple | `manuscript` | `http://purl.org/coar/resource_type/c_0040` |
| Multiple | `musical notation` | `http://purl.org/coar/resource_type/c_18cw` |
| Multiple | `peer review` | `http://purl.org/coar/resource_type/H9BQ-739P/` |
| Multiple | `research proposal` | `http://purl.org/coar/resource_type/c_baaf` |
| Multiple | `research protocol` | `http://purl.org/coar/resource_type/YZ1N-ZFT9/` |
| Multiple | `software` | `http://purl.org/coar/resource_type/c_5ce6` |
| Multiple | `source code` | `http://purl.org/coar/resource_type/QH80-2R4E/` |
| Multiple | `technical documentation` | `http://purl.org/coar/resource_type/c_71bd` |
| Multiple | `transcription` | `http://purl.org/coar/resource_type/6NC7-GK9S/` |
| Multiple | `workflow` | `http://purl.org/coar/resource_type/c_393c` |
| Multiple | `other` | `http://purl.org/coar/resource_type/c_1843` |

> 公式別表【Ver2.0】には74語が掲載されています。
> 2026年7月16日に取得したHTMLを対象に、各語彙に一つずつある `rdf:resource` の項目を計数しました。
> 別表には、COAR Resource Types Vocabulary自体の版番号は明示されていません。

### 非推奨

`rdf:resource` を省略した次の記述は、使用できません。

```xml
<dc:type>departmental bulletin paper</dc:type>
```

### 入力例

```xml
<dc:type rdf:resource="http://purl.org/coar/resource_type/c_6501">journal article</dc:type>
<dc:type rdf:resource="http://purl.org/coar/resource_type/c_6501">departmental bulletin paper</dc:type>
<dc:type rdf:resource="http://purl.org/coar/resource_type/c_db06">doctoral thesis</dc:type>
<dc:type rdf:resource="http://purl.org/coar/resource_type/c_ddb1">dataset</dc:type>
<dc:type rdf:resource="http://purl.org/coar/resource_type/c_6501">article</dc:type>
```

### マッピング

| 要素 | junii2 |
|------|--------|
| `dc:type` | NIItype（NII資源タイプ） |

> 出典：上記のJPCOARスキーマ 2.0 公式説明ページ（#15）および資源タイプ語彙別表【Ver2.0】
