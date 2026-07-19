# コントリビューションガイド

## ようこそ

本リポジトリへのコントリビューションをお待ちしています。

## フローチャートの追加

フローチャートページ作成の流れは以下を参照してください：

- **構成・記号凡例・3層の原則**: [decision-trees/CONVENTIONS.md](decision-trees/CONVENTIONS.md)
- **作成手順**: [jpcoar-flowchart スキル](.claude/skills/jpcoar-flowchart/SKILL.md)
- **要素定義のまとめ**: [reference/_TEMPLATE_element_rules.md](reference/_TEMPLATE_element_rules.md)（コピーして作成）
- **必須度・xml:lang要件**: `reference/` 配下の対照表に準拠

## 文書品質チェック

Pull Request と main への push では、CI が `decision-trees/*.md` の Mermaid 構文と、すべての Markdown に含まれる内部リンクを必須チェックします。
外部リンクは一時的な到達不能で PR を止めないよう、手動実行で確認する警告チェックです。

ローカルでは、Mermaid CLI と lychee を導入して次のコマンドで再現できます。

```bash
npx --yes @mermaid-js/mermaid-cli@11.15.0 --input decision-trees/title.md --output /tmp/title.md
lychee --offline --config lychee.toml '**/*.md'
```

Mermaid の出力先は元ファイルを上書きしない一時ファイルにしてください。

## Issue

バグ報告やフローチャート追加のリクエストは所定のテンプレートをご利用ください。

## Pull Request

1. このリポジトリをフォーク
2. ブランチを作成 (`git checkout -b feature/your-feature`)
3. 変更をコミット (`git commit -m 'Add your feature'`)
4. プッシュ (`git push origin feature/your-feature`)
5. Pull Requestを作成

## ライセンス

- 自作コンテンツ: CC0
- LODE-BD 本体は同梱せず DOI 参照
