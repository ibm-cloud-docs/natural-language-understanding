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

# カスタマイズ
{: #customizing}

[{{site.data.keyword.knowledgestudiofull}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://ibm.biz/watsonknowledgestudio) では、お客様のドメインに固有のカスタム・エンティティーおよび関係を識別するカスタム・モデルを使用して {{site.data.keyword.nlushort}} を拡張することができます。
{: shortdesc}

## カスタム・モデルの使用を始める
{: #getting-started-with-custom-models}

> {{site.data.keyword.nlushort}} 無料プランでは、カスタム・モデルのサイズとパフォーマンスが制限されています。 最大限にカスタム・モデルをテストするには、{{site.data.keyword.nlushort}} 標準プランの使用が必要になります。

1. {{site.data.keyword.nlushort}} をまだ使用していない場合は、[使用を開始](/docs/services/natural-language-understanding?topic=natural-language-understanding-getting-started)します。
2. [{{site.data.keyword.knowledgestudioshort}} の使用を開始します](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutintro#wks_tutintro)。
3. [{{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutml_intro#wks_tutml_intro)を使用して機械学習モデルを作成します。
4. [モデルを {{site.data.keyword.nlushort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#wks_manlu) にデプロイします
5. お客様のモデルを使用するには、API 要求の[エンティティー ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/natural-language-understanding#entities){: new_window} オプションまたは[関係 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/natural-language-understanding#relations){: new_window} オプションでデプロイした`モデル`を指定します。
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
        curl --user "apikey":"{apikey}" \
        "{url}/v1/analyze?version=2018-09-21" \
        --request POST \
        --header "Content-Type: application/json" \
        --data @parameters.json
        ```
        {: pre}

## カスタム・モデルの削除
{: #deleting-a-custom-model}

{{site.data.keyword.nlushort}} の請求額は、[価格プラン](https://www.ibm.com/cloud/watson-natural-language-understanding/pricing)に応じて、{{site.data.keyword.nlushort}} にデプロイしたカスタム・モデルの数によって決定されます。使用しなくなったモデルについて課金されることがないように、[{{site.data.keyword.knowledgestudioshort}}を使用してモデルをアンデプロイする](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#undeploy-view-model)か、または**[モデルの削除](https://{DomainName}/apidocs/natural-language-understanding#delete-model)**メソッドを使用してモデルをアンデプロイしてください。

curl 要求の例:

```bash
curl --user "apikey":"{apikey}" \
"{url}/v1/models/{model_id}?version=2018-10-30" \
--request DELETE
```
{: pre}


## カスタム・モデルの言語サポート
{: #language-support-for-custom-models}

[言語サポート](/docs/services/natural-language-understanding?topic=natural-language-understanding-language-support)ページの表の*「カスタム・モデル・サポート」*列で、各言語でサポートされているカスタム・モデルを確認してください。

### カスタム・モデル・エンティティーをターゲットにした評判
{: #targeted-sentiment-for-custom-entities}

(英語のみ) entities オブジェクトで `sentiment: true` オプションを設定することで、サービスで検出された各カスタム・モデル・エンティティーの評判スコアを取得できます。その他の言語では、カスタム・モデル・エンティティーをターゲットにした評判はサポートされません。
