---

copyright:
  years: 2015, 2018
lastupdated: "2018-01-16"

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

# カスタマイズ

[{{site.data.keyword.knowledgestudiofull}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://ibm.biz/watsonknowledgestudio) では、お客様のドメインに固有のカスタム・エンティティーおよび関係を識別するカスタム・モデルを使用して {{site.data.keyword.nlushort}} を拡張することができます。
{: shortdesc}

## カスタム・モデルの使用を始める

> {{site.data.keyword.nlushort}} 無料プランでは、カスタム・モデルのサイズとパフォーマンスが制限されています。フル・エクステントに対してカスタム・モデルをテストするには、{{site.data.keyword.nlushort}} 標準プランの使用が必要になります。

1. {{site.data.keyword.nlushort}} をまだ使用していない場合は、[使用を開始](/docs/services/natural-language-understanding/getting-started.html)します。
1. [{{site.data.keyword.knowledgestudioshort}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/us-en/marketplace/supervised-machine-learning/purchase#product-header-top) にアクセスし、[オンライン・ダッシュボード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://gateway.watsonplatform.net/knowledge-studio/ui/dashboard/) を使用してログインします。
1. {{site.data.keyword.knowledgestudioshort}} の[資料](/docs/services/knowledge-studio/index.html)を表示し、カスタム・モデル (アノテーター) を作成して {{site.data.keyword.nlushort}} にデプロイする方法を確認します。
1. お客様のモデルを使用するには、API 要求の[エンティティー ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/#entities){: new_window} オプションまたは[関係 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/#relations){: new_window} オプションでデプロイした`モデル`を指定します。
    - *parameters.json* ファイルの例:

        ```json
        {
          "url": "www.url.example",
          "features": {
            "entities": {
              "model": "your-model-id-here"
            },
            "relations": {
              "model": "your-model-id-here"
            }
          }
        }
        ```
        {: codeblock}
    
    - curl 要求の例:

        ```bash
        curl -X POST \
        -H "Content-Type: application/json" \
        -u "{username}":"{password}" \
        -d @parameters.json \
        "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
        ```
        {: pre}

