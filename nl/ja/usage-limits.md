---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-16"

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

# 使用制限

以下の使用制限と制約事項が {{site.data.keyword.nlushort}} サービス・インスタンスに適用されます。
{: shortdesc}

## 分析済みテキスト制限

{{site.data.keyword.nlushort}} は、50,000 文字を超える 1 バイト文字またはマルチバイト文字を含む分析済みテキストを切り捨てます。要求内でこの制限が適用されるテキストを表示するには、`return_analyzed_text` パラメーターを `true` に設定します。

`limit_text_characters` パラメーターを使用して、文字数制限をより小さく設定できます。コンテンツの小さな部分のみを分析したい場合、この方法は余分なコストの削減に役立ちます。

パラメーター・オブジェクトの例:
```json
{
  "url": "ibm.com",
  "limit_text_characters": 10000,
  "return_analyzed_text": true,
  "features": {
    "concepts": {}
  }
}
```

## 同時要求制限

各 {{site.data.keyword.nlushort}} サービス・インスタンスは、同時要求が 30 までに制限されています。システムで異常に大量のトラフィックが発生している場合、ライト・プランと標準プランでは、サービス・インスタンスに関してこの制限が引き下げられることがあります。例えば、1 つのサービス・インスタンスから 35 の同時要求を行うアプリケーションは、同時要求制限を 5 超過します。
この 5 つの要求は、`「429: 要求が過多 (Too Many Requests)」`エラーを返します。

同時要求制限を大きくするには、[サポート・チケットを開きます](https://ibm.biz/ibmcloudsupport)。


## 言語サポート

サービスの使用方法によって、適用される言語制限は異なります。詳しくは、[『言語サポート』](language-support.html)ページを参照してください。


