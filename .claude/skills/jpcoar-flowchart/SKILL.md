---
name: jpcoar-flowchart
description: >-
  Use when creating or revising a JPCOAR schema element input flowchart in this
  repo (decision-trees/*.md) and its element-rules reference (reference/*_rules.md).
  Triggers include requests like "作成者のフローチャートを作って", "日付の入力ガイドを作成",
  "〇〇要素のルールをまとめて", or revising an existing flowchart against the official
  schema and DOI requirements. Encodes the 3-step process: (1) summarize the official
  definition, (2) build the flowchart adding JaLC/Crossref DOI requirements, (3)
  cross-check both against sources.
---

# JPCOAR フローチャート作成スキル

JPCOARスキーマ 2.0 の1プロパティについて、公式定義のまとめ（`reference/<element>_rules.md`）と入力フローチャート（`decision-trees/<element>.md`）を作成・改訂するための手順。

## 大原則: 3層を常に分離する

混同が誤りの主因。出力では必ず区別する（詳細は [decision-trees/CONVENTIONS.md](../../../decision-trees/CONVENTIONS.md) 第5節）。

1. **スキーマ層** — 公式説明ページ（M/MA、繰返、属性、非推奨）
2. **DOI登録層** — [対照表](../../../reference/JPCOAR_JaLC_Crossref_requirements.md)（JaLC/Crossref の必須・条件付必須・任意・推奨、`xml:lang="en"` 必須など）
3. **本ガイド運用方針** — CONVENTIONS.md（例: `xml:lang` は原則付与）

## 入力資料

- 公式説明ページ: `https://schema.irdb.nii.ac.jp/ja/schema/2.0/<番号>`（番号は [reference/JPCOARschema_guide.md](../../../reference/JPCOARschema_guide.md)）。WebFetch で取得する。
- DOI要件: [reference/JPCOAR_JaLC_Crossref_requirements.md](../../../reference/JPCOAR_JaLC_Crossref_requirements.md)
- 既存の完成例: [decision-trees/title.md](../../../decision-trees/title.md) / [reference/title_rules.md](../../../reference/title_rules.md)

---

## ステップ1: 公式定義をまとめる → `reference/<element>_rules.md`

1. [reference/JPCOARschema_guide.md](../../../reference/JPCOARschema_guide.md) で対象の項番・下位項目を確認。
2. 公式説明ページ（主要素＋下位項目すべて）を WebFetch で取得。下位項目・入れ子は**1つずつ**取得する。
3. [reference/_TEMPLATE_element_rules.md](../../../reference/_TEMPLATE_element_rules.md) をコピーして埋める。
4. **この段階では公式の記述のみ**。DOI要件・運用方針・独自概念を混ぜない。
5. 抽出する項目: 要素名 / 記入レベル(M・MA等) / 繰返回数 / 属性と統制語彙 / 下位項目構造 / 記述ルール / 非推奨 / 入力例 / マッピング。
6. 完成したら [reference/README.md](../../../reference/README.md) の収録資料表に1行追加。

## ステップ2: フローチャートを作る → `decision-trees/<element>.md`

1. [decision-trees/title.md](../../../decision-trees/title.md) の構成を雛形にする（CONVENTIONS.md 第1節の順序）。
2. 記号凡例・記入レベル凡例・`xml:lang` 方針は **CONVENTIONS.md を参照**し、全文の再掲はしない。
3. ステップ1の `*_rules.md` を要素・属性・入力例の典拠にする。
4. **DOI要件の分岐を対照表から織り込む**:
   - 「DOI登録先は?（登録しない / JaLC / Crossref）」を上流の判断に置く。
   - 対象が**書籍系か**で Crossref の `xml:lang="en"` 必須などが変わる要素は、資源タイプ分岐を追加。
   - 対照表の語（必須 / 条件付必須 / 任意 / 推奨）を**そのまま**使う（言い換えない）。
5. Mermaid は `flowchart TD`。GitHub で描画されるか構文を意識する（ラベル内の特殊文字に注意）。
6. [decision-trees/README.md](../../../decision-trees/README.md) と [README.md](../../../README.md) の一覧表の状態を更新。

## ステップ3: 照合・検証（省略しない）

完成物を両典拠に突き合わせ、以下をチェックする。今回これで `xml:lang` の取り違えを発見した。

- [ ] 公式に**ない概念を足していない**か（独自区分は「運用上」と明記したか）
- [ ] 記入レベル・繰返・属性が `*_rules.md`（＝公式）と一致するか
- [ ] DOI要件の語（必須/条件付必須/任意/**推奨**）を取り違えていないか（特に JaLC の「任意」と「推奨」）
- [ ] スキーマ層・DOI層・運用方針の3層が混ざっていないか
- [ ] Crossref の `xml:lang="en"` 必須・ORCID限定・書籍系の対象タイプを正しく反映したか
- [ ] フローチャート / 対応表 / 注記 / 入力例が相互に矛盾しないか
- [ ] 一覧表（README 2か所）の状態を更新したか

---

## よくある落とし穴（過去の実例）

- **公式にない概念の追加**: 「翻訳タイトル」を独自カテゴリにしてしまう等。公式の用語・区分に厳密に従う。
- **「推奨」と「任意」の混同**: 対照表は要素ごとに使い分けている。タイトル `xml:lang` は JaLC で「任意」、作成者名は「推奨」。
- **3層の混同**: スキーマの MA、DOI要件、ガイド方針を1文に潰さない。
- **入れ子要素の単純化**: 作成者(#3)等は識別子・姓名・姓・名・別名・所属の入れ子＋条件付必須が多い。ステップ1で構造を先に固める。
