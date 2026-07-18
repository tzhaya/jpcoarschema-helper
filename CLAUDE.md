# CLAUDE.md

このファイルは、このリポジトリで作業する Claude Code 向けのガイドです。

## このリポジトリの性質

JPCOARスキーマ 2.0 の各項目を、初心者が迷わず入力できるようにするための**ドキュメント集**です。コード、ビルド、テスト、依存関係はありません。成果物はすべて Markdown（Mermaid 図を含む）で、GitHub 上でそのまま描画されることを前提にしています。

- 手法の下敷き: FAO の LODE-BD 3.0（<https://doi.org/10.4060/cb2209en>）
- 利用シーン: **DOI登録（JaLC / Crossref）を重視**した機関リポジトリ（JAIRO Cloud）の登録作業
- 記述言語: 日本語

「ビルド」「テスト」に相当する検証は、CI による Mermaid 構文チェックと内部リンクチェックに加え、GitHub 上での描画や文書の意味が意図どおりかを目視で確認することです。

## 全体構造（最重要）

1プロパティにつき、**2つの対になるファイル**を作成します。両者は必ず整合させてください。

| 役割 | 場所 | 内容 |
|------|------|------|
| 公式定義のまとめ | [reference/](reference/)`<element>_rules.md` | 公式説明ページのみを典拠にした要素定義（記入レベル、繰返、属性、統制語彙、下位構造）。**DOI要件や運用方針を混ぜない** |
| 入力フローチャート | [decision-trees/](decision-trees/)`<element>.md` | `*_rules.md` を典拠に、DOI要件の分岐を織り込んだ Mermaid フローチャート、対応表、注記 |

共通の骨格、凡例、方針は [decision-trees/CONVENTIONS.md](decision-trees/CONVENTIONS.md) に集約されています。各ページに再掲せず、同ファイルを参照してください。

フローチャートの作成・改訂時は、`jpcoar-flowchart` スキル（[.claude/skills/jpcoar-flowchart/SKILL.md](.claude/skills/jpcoar-flowchart/SKILL.md)）に定義された手順に従ってください。
内容の照合後は、`cognitive-rhythm-writing` と、その依存規範である `japanese-tech-writing` を使用して文章を推敲します。

## 最重要の原則: 3層を混同しない

要件は、次の3層を必ず区別して記述します。混同は誤りの主因です。詳細は [decision-trees/CONVENTIONS.md](decision-trees/CONVENTIONS.md) 第5節を参照してください。

| 層 | 典拠 | 例 |
|----|------|----|
| **スキーマ層** | [公式説明ページ](https://schema.irdb.nii.ac.jp/ja/schema) / `reference/*_rules.md` | `dc:title` は M（必須）、`xml:lang` は MA |
| **DOI登録層** | [対照表](reference/JPCOAR_JaLC_Crossref_requirements.md) | タイトルの `xml:lang` は JaLC＝任意 / Crossref＝必須 |
| **本ガイドの運用方針** | [decision-trees/CONVENTIONS.md](decision-trees/CONVENTIONS.md) | `xml:lang` は入力漏れ防止のため原則付与 |

頻出する注意点:

- **DOI要件の語（必須 / 条件付必須 / 任意 / 推奨）はそのまま使い、言い換えない**でください。特に「任意」と「推奨」は要素ごとに使い分けられています。例: タイトルの `xml:lang` は JaLC で任意、作成者名は推奨です。
- **公式に存在しない概念を独自に追加しない**でください。運用上の区分を設ける場合は、「運用上の区分」と明記してください。

## 各ページ冒頭の「この項目の性質」（4観点）

すべてのフローチャートページの冒頭に、入力作業の性質を次の4観点の表で記載します。定義は [decision-trees/CONVENTIONS.md](decision-trees/CONVENTIONS.md) 第8節を参照してください。これはプロジェクト標準であり、ROADMAP の優先度判断にも使われます。

| 観点 | 問い |
|------|------|
| 入力の型 | 解釈型（統制語彙から選ぶ）／転記型（書誌から写す）／調査型（外部を調べる） |
| 他項目への影響 | その選択が他項目の必須度や値に波及するか |
| 事前調査 | 入力前に調べることがあるか。情報源はどこか |
| 誤入力の影響 | 間違えると何が起きるか。DOI登録エラーなどの具体的実害はあるか |

**解釈型**かつ他項目への影響が大きい項目ほど、フローチャートを丁寧に整備する価値があります。

## 新しいプロパティを追加・改訂するとき

`jpcoar-flowchart` スキルの4ステップに従ってください。

1. **公式定義をまとめる**
   - 作成先: `reference/<element>_rules.md`
   - [reference/JPCOARschema_guide.md](reference/JPCOARschema_guide.md) で項番を確認します。
   - 公式説明ページ（`https://schema.irdb.nii.ac.jp/ja/schema/2.0/<番号>`）を取得します。下位項目は1つずつ確認してください。
   - [reference/_TEMPLATE_element_rules.md](reference/_TEMPLATE_element_rules.md) を雛形として使用します。
   - **この段階では公式記述のみ**を記載し、DOI要件や本ガイドの運用方針を混ぜないでください。

2. **フローチャートを作る**
   - 作成先: `decision-trees/<element>.md`
   - [decision-trees/title.md](decision-trees/title.md) を雛形として使用します。
   - 冒頭に「この項目の性質」の4観点表を記載します。
   - `reference/<element>_rules.md` を要素・属性の典拠とします。
   - [DOI要件の対照表](reference/JPCOAR_JaLC_Crossref_requirements.md)から、登録しない / JaLC / Crossref の分岐や、書籍系での `xml:lang="en"` 必須などの要件を織り込みます。
   - Mermaid は `flowchart TD` を使用します。

3. **照合・検証する（省略禁止）**
   - 公式にない概念を追加していないか確認します。
   - 記入レベル、繰返、属性が `*_rules.md` と一致するか確認します。
   - DOI要件の用語を取り違えていないか確認します。
   - スキーマ層、DOI登録層、本ガイドの運用方針が混ざっていないか確認します。
   - Mermaid が GitHub 上で描画できる構文か、内部リンクが切れていないか確認します。

4. **文章を推敲する（省略禁止）**
   - `cognitive-rhythm-writing` と `japanese-tech-writing` を使用します。
   - 冒頭は、入力時に生じる具体的な迷いや判断の差から始めます。
   - 一文一行を基本とし、段落ごとに一つの論点を扱います。
   - 文書の進行だけを述べる予告や総括を置かず、対象の性質に基づいて節をつなぎます。
   - 推敲によって、公式定義、記入レベル、DOI要件の用語、Mermaidの分岐、XML例の意味を変更しません。
   - 推敲後にステップ3の照合をもう一度行います。

## 一覧表の更新（追加・状態変更時に必須）

プロパティを追加したとき、または状態を変更したときは、フローチャート一覧の正本を更新してください。

- [decision-trees/README.md](decision-trees/README.md) の一覧表（フローチャート一覧・進捗の正本）
- 新規ルールを追加した場合は [reference/README.md](reference/README.md) の収録資料表

## 整備の優先順位

[ROADMAP.md](ROADMAP.md) に着手順があります。**DOI登録の必須項目**を最優先とし、加えて**入力時の判断負荷（解釈型かどうか）**を優先度の基準とします。

ID登録・資源タイプを先に固めると、各フローチャート冒頭の「DOI登録先」分岐が定まり、後続の `xml:lang` 必須度を一貫させられます。

## 編集時の基本方針

- 既存文書の用語、表記、Markdown 構造を尊重してください。
- 関係のないファイルや記述を変更しないでください。
- 公式情報を参照した箇所は、出典を追跡できる形で記述してください。
- 推測を公式要件として断定しないでください。不明点は典拠を確認し、確認できない場合はその旨を明記してください。
- `decision-trees/*.md` の作成・改訂後は、`cognitive-rhythm-writing` と `japanese-tech-writing` による推敲を行ってください。
- 変更後は、対になる `reference/*_rules.md` と `decision-trees/*.md` の整合性、および関連する一覧表を確認してください。
