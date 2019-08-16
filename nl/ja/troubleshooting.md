---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-25"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}

# トラブルシューティング
{: #troubleshooting}

{{site.data.keyword.nlushort}} で問題が発生した場合に役立つ可能性があるトラブルシューティングのヒントを以下に示します。
{:shortdesc}

## エンティティーと関係のエンティティー・タイプが一致していない
{: #inconsistent-entity-types}

エンティティー・フィーチャーと関係フィーチャーのエンティティー・タイプ・システムは、常に一致するわけではありません。 言語とバージョン日付によっては、関係の結果に、エンティティーの結果に示されるエンティティー・タイプとは異なるエンティティー・タイプが含まれていることがあります。 詳細については、[エンティティーのタイプとサブタイプ](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-type-systems)および[関係タイプ](/docs/services/natural-language-understanding?topic=natural-language-understanding-relation-type-systems)を参照してください。 

## 言語検出の誤り
{: #incorrect-language-detection}

100 文字未満のテキストでは、自動言語検出が正確に行われないことがあります。 サービスがテキストの正しい言語を検出しない場合は、ユーザーが[自動言語検出をオーバーライド](/docs/services/natural-language-understanding?topic=natural-language-understanding-overriding-language-detection)できます。

## 要求が多すぎる
{: #too-many requests}

「429: 要求が多すぎる (Too Many Requests)」エラーが発生する場合は、サービス・インスタンスの同時要求制限に達している可能性があります。 詳しくは、[使用制限](/docs/services/natural-language-understanding?topic=natural-language-understanding-usage-limits#concurrent-requests)ページを参照してください。

## Web ページ分析で予期しない結果が返される
{: #unexpected-webpage-results}

Web ページの分析で予期しない結果が返されることがあります。 調査するには、**return_analyzed_text** パラメーターを `true` に設定して、要求で分析されている実際のテキストを調べてください。 [Web ページ・クリーニング](/docs/services/natural-language-understanding?topic=natural-language-understanding-analyzing-webpages#webpage-cleaning)で不要なテキストが十分に削除されていない場合は、[**xpath**](/docs/services/natural-language-understanding?topic=natural-language-understanding-analyzing-webpages#xpath)パラメーターを使用して、分析対象をページの特定のエレメントに絞り込むことを検討してください。

## 特定の結果の説明
{: #explanations-for-results}

{{site.data.keyword.nlushort}} には、特定の要求で特定の結果が返された理由を調べるための診断ツールが用意されていません。 このサービスは、可能な限り多くのテキスト・サンプルで正確な結果が得られるように設計されていますが、使用している機械学習モデルの性質上、人間の視点から見て正しい結果が返されるという保証はありません。






